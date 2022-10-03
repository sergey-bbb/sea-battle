# sea-battle
# МОРСКОЙ БОЙ
import random
area = [[' ', ' ', ' ', ' ', ' ', ' '],
        [' ', ' ', ' ', ' ', ' ', ' '],
        [' ', ' ', ' ', ' ', ' ', ' '],
        [' ', ' ', ' ', ' ', ' ', ' '],
        [' ', ' ', ' ', ' ', ' ', ' '],
        [' ', ' ', ' ', ' ', ' ', ' '],
        ]
boat = [[0, 0], [0, 1], [0, 2], [0, 3]]
palubi = 4

# Решение:
def random_boat():
  global boat
  x = random.randint(0, 4)
  y = random.randint(0, 4)
  d = random.randint(0, 1)
  if d == 0:
    boat = [[x, y], [x, y+1], [x, y+2], [x, y+3]]
  else:
    boat = [[x, y], [x+1, y], [x+2, y], [x+3, y]]


def show_area():
  for row in area:
    print('|'.join(row))
    print('-'*12)

def striking():
  global palubi      #---
  print('номер столбца:')
  stolbec = int(input())
  print('номер ряда:')
  ryad = int(input())

  if [ryad, stolbec] in boat:
    if area[ryad][stolbec] != '#':
      print('Цель поражена')
      area[ryad][stolbec] = '#'
      palubi = palubi - 1
      if palubi == 0:
        print('Победа')
  else:
    print('Цель не сбита')
    area[ryad][stolbec] = '0'


show_area()
random_boat()
for i in range(10):
  striking()
  show_area()
