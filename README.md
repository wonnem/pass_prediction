[Deployment](https://img.shields.io/badge/Python-3.8+-blue)
내용 추가
#1 

```markdown
# 🎓 pass_prediction: 대학교 입시결과 예측 모델

> 고등학교 학생의 학생부 내신 성적, 모의고사 점수 및 주요 입시 지표 데이터를 기반으로 대학교 합격 가능성을 분석하고 예측하는 머신러닝 프로젝트입니다.

---

## 1. Hero
`pass_prediction`은 복잡한 입시 데이터 분석을 자동화하고, 머신러닝 모델을 통해 신뢰도 높은 합격 예측 결과를 도출하기 위해 개발되었습니다. 과거 합·불 데이터를 바탕으로 변수 간의 상관관계를 분석하고 최적의 분류 모델을 훈련합니다.

### 🛠 Tech Stack
- **Language:** Python 3.8+
- **Environment:** Jupyter Notebook
- **Libraries:** Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn

---

## 2. Demo
> 💡 *성적 입력 데이터에 따른 모델의 예측 스크린샷이나 탐색적 데이터 분석(EDA) 시각화 그래프(예: 특성 중요도, 혼동 행렬 등)를 이곳에 첨부하면 좋습니다.*

### 주요 시각화 예시
- **Feature Importance Plot:** 합격 예측에 가장 큰 영향을 미치는 주요 과목 및 요소 분석
- **Confusion Matrix:** 예측 모델의 정확도, 정밀도, 재현율 시각화

---

## 3. Features
- **데이터 전처리 및 정규화:** 누락된 데이터 처리, 학년별 내신 반영 비율 계산 및 모의고사 백분위 변환 표준화
- **탐색적 데이터 분석 (EDA):** 성적 추이 분석 및 합격/불합격 그룹 간의 유의미한 데이터 분포 시각화
- **머신러닝 기반 분류 (Classification):** Scikit-learn 기반 분류 알고리즘(예: Logistic Regression, Random Forest, 이진 분류 모델 등) 적용 및 성능 비교
- **맞춤형 합격 확률 예측:** 새로운 학생 데이터 입력 시 목표 대학/학과에 대한 합격 가능성을 확률 값으로 제시

---

## 4. Architecture
본 프로젝트는 데이터 수집부터 최종 예측 결과 도출까지 파이프라인 형태로 설계되었습니다.


```

[교내외 입시 Raw Data]
│
▼
[데이터 전처리 및 Feature Engineering] ── 결측치 정제 및 인코딩
│
▼
[탐색적 데이터 분석 (EDA)] ───────────── 상관관계 및 분포 시각화
│
▼
[모델 학습 및 튜닝] ────────────────── Scikit-learn 분류 모델 훈련
│
▼
[성능 검증 (Evaluation)] ───────────── Accuracy, F1-Score 평가
│
▼
[합격 예측 결과 출력 (Inference)]

```

---

## 5. Runbook
이 프로젝트를 로컬 환경에서 복제하고 실행하는 방법입니다.

### 사전 요구 사항 (Prerequisites)
- Python 3.8 이상 설치 필요
- Jupyter Notebook 또는 JupyterLab 설치 필요

### 설치 및 환경 세팅
1. 레포지토리를 클론합니다.
   ```bash
   git clone [https://github.com/wonnem/pass_prediction.git](https://github.com/wonnem/pass_prediction.git)
   cd pass_prediction

```

2. 필요한 라이브러리를 설치합니다.
```bash
pip install pandas numpy scikit-learn matplotlib seaborn notebook

```



### 실행 방법

1. 터미널에서 Jupyter Notebook을 실행합니다.
```bash
jupyter notebook

```


2. 웹 브라우저가 열리면 아래 메인 노트북 파일을 선택하여 실행합니다.
* `우송고_30723_이혜원_pass_prediction.ipynb`


3. 노트북의 각 셀(Cell)을 순서대로 실행(`Shift + Enter`)하여 데이터 전처리 및 모델 학습을 진행합니다.

---

## 6. Troubleshooting

### Q1. 데이터 로드 시 인코딩 오류 (`UnicodeDecodeError`)가 발생합니다.

* **원인:** 한국어 입시 데이터 파일(CSV, Excel)의 인코딩이 `UTF-8`이 아닌 `CP949`(또는 `EUC-KR`)로 저장되어 있을 때 발생합니다.
* **해결책:** `pd.read_csv()` 함수 내부의 encoding 옵션을 변경해 줍니다.
```python
# 변경 전
df = pd.read_csv('data.csv')
# 변경 후
df = pd.read_csv('data.csv', encoding='cp949')

```



### Q2. `ModuleNotFoundError: No module named 'sklearn'` 에러가 뜹니다.

* **원인:** 가상환경 또는 로컬 환경에 머신러닝 라이브러리가 설치되지 않았습니다.
* **해결책:** 터미널에서 다음 명령어를 실행하여 라이브러리를 다시 설치해 주세요.
```bash
pip install scikit-learn

```



### Q3. 그래프 출력 시 한글 깨짐 현상이 발생합니다.

* **원인:** Matplotlib의 기본 폰트가 한글을 지원하지 않기 때문입니다.
* **해결책:** 노트북 최상단에 아래 코드를 추가하여 맑은 고딕(Windows) 또는 애플고딕(Mac)으로 폰트를 설정해 주세요.
```python
import matplotlib.pyplot as plt
plt.rc('font', family='Malgun Gothic') # Windows 기준
# plt.rc('font', family='AppleGothic') # Mac 기준
plt.rcParams['axes.unicode_minus'] = False



