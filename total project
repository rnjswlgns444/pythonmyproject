import pygame
import random
import os
import csv

#필요한 변수들
done = False
timetable = {}
day  = ['월','화','수','목','금']

#처음 메뉴 생성
def totalprogram():
  print('----------------')
  print('1.폭탄 피하기 게임')
  print('2.계획표')
  print('3.오늘 뭐 먹지?')
  print('4. 종료')
  
  a = int(input('원하는 메뉴를 입력하시오'))
  
  if a == 1:
  
    runGame()
    pygame.quit()
    totalprogram()
  elif a == 2:
    menu()
    totalprogram()
  elif a ==3:
    programmenu()
    totalprogram()
  elif a == 4:
    exit()
  else:
    print('다시 입력하시오')

#폭탄 피하기 게임    
def runGame():
  pygame.init()
  BLACK = (0,0,0)
  size = [800,600]
  screen = pygame.display.set_mode(size)
  clock = pygame.time.Clock()
  
  bomb_image = pygame.image.load('bomb.png') #이미지 필요
  bomb_image = pygame.transform.scale(bomb_image, (50,50))
  bomb = []
  
  for i in range(5):
    rect = pygame.Rect(bomb_image.get_rect())
    rect.left = random.randint(0,size[0])
    rect.top = -100
    dy = random.randint(3,9)
    bombs.append({'rect':rect, 'dy':dy})

  person_image = pygame.image.load('person.png')
  person_image = pygame.transform.scale(person_image, (100,100))
  person.left = size[0]//2 - person.width//2
  person.top = =size[1] - person.height
  person_dx = 0
  person_dy = 0
  
  global done
  while not done:
    clock.tick(30)
    screen.fill(BLACK)
    
    for event in pygame.event.get():
      if event.type == pygame.QUIT:
        done = True
        break
      elif event.type == pygame.KEYDOWN:
        if event.key == pygame.K_LEFT:
          person_dx = -5
        elif event.key == pygame.K_RIGHT:
          person_dx = 5
        elif event.type == pyygame.KEYUP:
          if event.key == pygame.K_LEFT:
            person_dx = 0
          elif event.key == pygame.K_RIGHT:
            person_dx = 0
    for bomb in bombs:
      bomb['rect'].top > size[1]:
      bombs.remove(bomb)
      rect = pygame.Rect(bomb_image.get_rect())
      rect.left = random.randint(0, size[0])
      rect.top = -100
      dy = random.randint(3,9)
      bombs.append({'rect':rect, 'dy':dy})
    
    person.left = person.left + person_dx
    
    if person.left <0:
      person.left = 0
    elif person.left > size[0] - person.width:
      person.left = size[0] - person.width
    screen.blit(person_image,person)
    
    for bomb in bombs:
      if bomb['rect'].colliderect(person):
        done = True
      screen.blit(bomb_image, bomb['rect'])
    pygame.display.update()

#음식 추천 파일
  #음식 추가
def appendfood():
  appendfile = open(r"C:\Users\rnjsw\Desktop\food.txt","a")
  
  userinput = input('추가하려는 음식 입력')
  appendfile.write(' %s' %userinput)
  appendfile.close()

  #음식 추천받기
def recommendfood():
  infile = open(r"C:\Users\rnjsw\Desktop\food.txt", "r")
  
  for line in infile:
    lines = line.rstrip()
    want = lines.split()
  r = random.randint(0,len(want) -1)
  print(want[r])
#음식 추천 메뉴 하나로 묶기
def programmenu():
  while True:
    print('------------')
    print('1.음식 추가')
    print('2.음식 추천')
    print('3.종료')
    
    userwant = int(input('이용하려는 번호를 입력하시오'))
    
    if userwant == 1:
      appendfood()
    elif userwant == 2:
      recommendfood()
    elif userwant == 3:
      break
    else:
      print('다시 입력하시오')

#계획표 작성 프로그램
def menu():
  while True:
    print('1.시간표 입력(프로그램 시작시)')
    print('2.시간표 수정')
    print('3.시간표 출력')
    print('4.종료')
    
    input_want = int(input('번호를 입력하시오'))
    
    if input_want == 1:
      enter_timetavle()
    elif input_want == 2:
      modify_timetable()
    elif input_want ==3:
      output_timetable()
    elif input_want == 4:
      break
    else:
      print('다시 입력하세요.')
  #시간표 입력
def enter_timetable():
  for i in day:
    print('%s요일 시간표를 입력핫시오(계획을 끝내려면 "끝"을 입력하기)'%i)
    
    day_timetable = []
    j=0
    while True:
    day_timetable.append(inputt('계획을 입력하시오'))
    if day_timetable[j] == '끝':
      break
    j+=1
    
    day_timetable.pop()
    timetable[i] = day_timetable
  #시간표 출력
def output_timetable():
  input_day = input('조회할 요일을 입력하시오(요일 빼고)')
  
  if input_day in day:
    for k, name in enumerate(timetable[input_day]):
      print(k+1,name)
    print()
  else:
    print('다시 입력하시오')
    
  #시간표 수정
def modify_timetable():
  while True:
    modify_input = input('수정할 요일을 입력하시오(끝내려면 "없"을 입력하기)')
    
    if modify_input in day:
      day_timetable = timetable[modify_input]
      j=0
      
      while True:
        day_timetable.append(input('계획을 입력하시오(끝내려면 "끝"을 입력하기)'))
        
        if day_timetable[j] == '끝':
          break
        j+=1
        
      day_timetable.pop()
      timetable[modify_input] = day_timetable
    elif modify_input == '없':
      break
    else:
      print('다시 입력하시오')
          
