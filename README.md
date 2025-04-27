# Reinforcement Learning on MiniGrid

MiniGrid 환경에서 Q-Learning과 SARSA 알고리즘을 활용한 강화학습 실험
탐색 전략 비교 및 할인율 변화에 따른 학습 성능 분석

## 실험 환경 및 설정

| 항목           | 설정 값                         |
| -------------- | ---------------------------- |
| 환경           | MiniGrid-Empty-6x6-v0         |
| 알고리즘       | Q-Learning, SARSA             |
| 탐색 정책      | ϵ-greedy (ϵ=0.2)              |
| 학습률 (α)     | 0.01                          |
| 할인율 (γ)     | 0.1, 0.5, 0.9, 0.99           |
| 에피소드 수    | 100,000 / 500,000(SARSA) / 5,000,000(SARSA) / 10,000,000(SARSA) |


## 실험 결과
### Q-Learning 평균 보상
 ![image](https://github.com/user-attachments/assets/62cd3354-d05f-4394-a54b-aa469b60341b)
 
### Q-Learning - Q-value 분포 히스토그램
![image](https://github.com/user-attachments/assets/174015b9-2009-43cf-bb15-7ab74c94f567)

### Q-Learning - Policy Heatmap 
![image](https://github.com/user-attachments/assets/1dce13fb-0b56-474f-834a-21700386203d)
##### Policy Heatmap: 학습된 각 상태에서의 최적 행동을 시각화한 것
##### 대부분의 상태에서는 탐색이 이루어지지 않아 값이 -1로 표시되었으며 일부 상태에서는 최적 행동이 명확히 도출되었다. 
##### Q-Learning이 특정 경로에서만 학습이 집중되어 전체 상태 공간에서의 정책 수립이 제한적이었음을 나타낸다. 
##### 좌측 상단 및 하단 일부 상태에서는 에이전트가 상(0), 좌(2) 방향으로 움직이는 행동을 선택한 것으로 볼 때 해당 위치에서 목표로 향하는 경로를 학습한 것을 알 수 있다. 

### SARSA - Q-value 분포 히스토그램
![image](https://github.com/user-attachments/assets/3d3bf8c6-00ff-4f72-8097-a3ec6a77a446)

###### sarsa에서는 상태가 좌표 기반이 아닌 숫자형으로 표현되어 Q-table을 2차원 공간상에서 heatmap 형태로 시각화하는 것에 어려움이 있어 
###### Q-table 전체 값을 히스토그램으로 시각화하여, Q-value의 분포를 통해 학습 수렴 양상을 분석하였다
###### 히스토그램을 통해 각 상태별 최적 행동의 정책의 방향성을 확인하여 Q-table의 구조적 특성을 반영한 대체 시각화 방법으로 표현하였다

### Q-Learning vs SARSA 평균 보상 비교
![image](https://github.com/user-attachments/assets/6e1aaf3b-89ec-49e7-b7a4-0fc1650ed123)

### 학습 도중 에피소드별 성공률 
####  Q-Learning 
![image](https://github.com/user-attachments/assets/ee29ac35-cf98-48d1-9a55-edc67a196f0a)
##### Q-Learning은 약 50%에서 53% 사이의 성공률을 유지하며 비교적 안정적인 패턴 

#### SARSA 
![image](https://github.com/user-attachments/assets/a9d86c99-4b74-4be1-9fb4-055de74c4868)
##### SARSA는 비슷한 평균 성공률을 기록했으나 변동 폭이 더 크고 일부 구간에서 성공률이 급격히 하락하거나 상승하는 불안정한 양상

####  Q-Learning이 미래 보상을 기준으로 더 공격적으로 최적 정책을 형성하는 데 비해 SARSA는 현재 정책을 따라가는 보수적인 방식으로 인해 탐색 과정에서 일관된 성공률을 유지하는 데 한계를 보였음을 나타낸다


-----

### Q-Learning - γ 변화에 따른 reward 그래프
<p align="center">
  <img src="https://github.com/user-attachments/assets/e8f912ac-2c6c-480b-9762-f4044f9d9a2b" width="200"/>
  <img src="https://github.com/user-attachments/assets/9e445855-2b36-4b3e-b865-0bc2a238e4c6" width="200"/>
  <img src="https://github.com/user-attachments/assets/ba20768a-d986-4917-86ea-77a79c7672fc" width="200"/>
  <img src="https://github.com/user-attachments/assets/d3ac534e-5b1a-4d8f-baa3-86fd91677d2d" width="200"/>
</p>

### SARSA - γ 변화에 따른 reward 그래프
<p align="center">
  <img src="https://github.com/user-attachments/assets/80f9dcc6-35da-42cc-b961-cbaa2db8b5f5" width="200"/>
  <img src="https://github.com/user-attachments/assets/0e11b9fe-f128-40f4-8f52-50dfbbc4193c" width="200"/>
  <img src="https://github.com/user-attachments/assets/aacf339d-4e92-4d10-9ee5-23762a69d377" width="200"/>
  <img src="https://github.com/user-attachments/assets/94ded1cb-071d-4229-933e-a161aa4c51f1" width="200"/>
</p>

### Q-Learning - γ 값 변화에 따른 Q-value 분포
<p align="center">
  <img src="https://github.com/user-attachments/assets/a90b89ea-38b2-4007-98fe-2a1c135b438f" width="200"/>
  <img src="https://github.com/user-attachments/assets/f1562a7e-2263-46bc-aebf-398bb7439375" width="200"/>
  <img src="https://github.com/user-attachments/assets/6e617966-40a8-45f2-a555-414ca9832825" width="200"/>
  <img src="https://github.com/user-attachments/assets/b3d0b36e-b359-41ed-9ce5-4ad05e013492" width="200"/>
</p>


