# Generative-Fake-Voice-Detector-AI

### 주제

생성형 AI의 가짜(Fake) 음성 검출 및 탐지

### 주제선정 배경

최근 생성 AI 기술의 발전으로 인해 가짜 음성 합성이 점점 더 정교해지고 있다. 이러한 가짜 음성은 기존의 텍스트 기반 가짜 정보 유포 문제에 더해 새로운 위협이 되고 있다. 가짜 음성을 통해 유명인의 음성을 모방하거나 중요 인사의 발언을 조작할 수 있기 때문이다. 이는 개인 및 기업의 명예 실추, 금전적 피해, 사회적 혼란 등 다양한 문제를 야기할 수 있다.

따라서 가짜 음성을 신뢰할 수 있는 수준에서 검출하고 탐지할 수 있는 기술을 개발하여, 가짜 음성으로 인한 피해를 예방하고 생성 AI 기술이 건전하게 활용될 수 있는 환경을 조성하고자 한다.

또한 가짜 음성 탐지 기술은 음성인식, 스피커 인증, 대화 시스템 등 다양한 분야에서 활용될 수 있어 폭넓은 파급효과가 예상된다.

따라서 가짜 음성 검출 및 탐지 기술을 발전시킨다면 앞으로 대두될 수 있는 가짜 음성 문제에 선제적으로 대응할 수 있을 것으로 기대한다.

### 문제

5초 분량의 입력 오디오 샘플에서 영어 음성의 진짜(Real) 사람의 목소리와 생성 AI의 가짜(Fake) 사람의 목소리를 동시에 검출해내는 AI 모델 개발

- 학습 데이터는 방음 환경에서 녹음된 진짜(Real) 사람의 목소리 샘플과 방음 환경을 가정한 가짜(Fake) 사람의 목소리로 구성되어 있으며, 각 샘플 당 사람의 목소리는 1개이다.
- 평가 데이터는 5초 분량의 다양한 환경에서의 오디오 샘플로 구성되며, 샘플 당 최대 2개의 진짜(Real) 혹은 가짜(Fake) 사람의 목소리가 동시에 존재한다.
- Unlabel 데이터는 학습에 활용할 수 있지만 Label이 제공되지 않으며, 평가 데이터의 환경과 동일하다.

### Dataset Info

- **train [폴더]**
    - 55,438개의 학습 가능한 32kHz로 샘플링 된 오디오(ogg) 샘플
    - 방음 환경에서 녹음된 진짜 사람 목소리(Real) 샘플과 방음 환경을 가정한 가짜 생성 목소리(Fake) 샘플
    - 각 샘플 당 한 명의 진짜 혹은 가짜 목소리가 존재
- **test [폴더]**
    - 50,000개의 **5초 분량**의 32kHz로 샘플링 된 평가용 오디오(ogg) 샘플
    - TEST_00000.ogg ~ TEST_49999.ogg
    - 방음 환경 혹은 방음 환경이 아닌 환경 모두 존재하며, 각 샘플 당 최대 2명의 목소리(진짜 혹은 가짜)가 존재
- **unlabeled_data [폴더]**
    - 1,264개의 **5초 분량**의 학습 가능한 32kHz로 샘플링 된 Unlabeled 오디오(ogg) 샘플
    - 평가용 오디오(ogg) 샘플과 동일한 환경이지만 Label은 제공되지 않음
- **train.csv [파일]**
    - id : 오디오 샘플 ID
    - path : 오디오 샘플 경로
    - label : 진짜(real) 혹은 가짜(fake) 음성의 Class
- **test.csv [파일]**
    - id : 평가용 오디오 샘플 ID
    - path : 평가용 오디오 샘플 경로
- **sample_submission.csv [파일] - 제출 양식**
    - id : 평가용 오디오 샘플 ID
    - fake : 해당 샘플에 가짜 목소리가 존재할 확률 (0~1)
    - real : 해당 샘플에 진짜 목소리가 존재할 확률 (0~1)
**※ 모든 음성 데이터는 '영어' 언어를 바탕으로 구성되어 있다.**
