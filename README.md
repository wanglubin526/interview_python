# interview_python
# 整理面试题
"""
为了充分发挥GPU算力，需要尽可能多的将任务交给GPU执行，现在有一个任务数组，数组元素表示在这1秒内新增的任务个数且每秒都有新增任务，假设GPU最多一次执行n个任务，一次执行耗时1秒，在保证GPU不空闲情况下，最少需要多长时间执行完成
输入描述：
第一个参数为GPU一次最多执行的任务个数，取值范围[1, 10000]
第二个参数为任务数组长度，取值范围[1, 10000]
第三个参数为任务数组，数字范围[1, 10000]
输出描述：
执行完所有任务最少需要多少秒
输入：
3
5
1 2 3 4 5
输出：
6
"""
def main():
  try:
    cpu_num = eval(input())
    if cpu_num < 1 or cpu_num > 10000:
      raise Exception("输入的CPU个数超出规定范围!")
    arr_num = eval(input())
    if arr_num < 1 or arr_num > 10000:
      raise Exception("输入的任务数长度超出规定范围!")
    lis = list(map(int, input().split(" ")))
    if len(lis) != arr_num:
      raise Exception("输入的任务数组元素个数异常!")
    num = 0
    time = 0
    for i in lis:
      if i + num > cpu_num:
        num = i + num - cpu_num
      else:
        num = 0
      time += 1
    while num > 0:
      num -= cpu_num
      time += 1
    print(time)
  except Exception as e:
      print(e)
  except:
    print("程序异常！")
main()
