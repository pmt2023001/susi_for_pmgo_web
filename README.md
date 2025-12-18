# 수시 입시 결과 시각화 프로그램 (SUSI)

강원진학센터 입시분석팀에서 개발한 수시 입시 결과 분석 및 시각화 도구입니다.

## 📋 목차
- [프로그램 소개](#-프로그램-소개)
- [주요 기능](#-주요-기능)
- [설치 방법](#-설치-방법)
- [사용 방법](#-사용-방법)
- [파일 구조](#-파일-구조)
- [설정 방법](#-설정-방법)
- [문제 해결](#-문제-해결)
- [라이선스](#-라이선스)

## 🎯 프로그램 소개

본 프로그램은 수시 입시 결과 데이터를 효율적으로 분석하고 시각화하여, 입시 담당자와 학생들이 입시 현황을 쉽게 파악할 수 있도록 도와주는 도구입니다.

### 특징
- **직관적인 GUI**: Tkinter 기반의 사용자 친화적 인터페이스
- **다중 필터링**: 지역, 대학, 전형유형, 전형, 모집단위별 복합 검색
- **인터랙티브 시각화**: Plotly를 활용한 동적 차트와 그래프
- **상세 통계 분석**: 합격률, 평균 등급, 표준편차 등 포괄적 통계 제공
- **HTML 보고서**: 결과를 웹 페이지 형태로 출력하여 공유 가능

## ✨ 주요 기능

### 1. 데이터 분석
- **엑셀 파일 로드**: `.xlsx`, `.xls` 형식 지원
- **실시간 필터링**: 선택 조건에 따른 즉시 데이터 갱신
- **통계 계산**: 합격률, 평균 등급, 표준편차, 변동계수 등

### 2. 시각화
- **산점도**: 등급별 합격/불합격 분포
- **히스토그램**: 등급별 지원자 분포
- **도넛 차트**: 결과별 비율 시각화
- **막대 그래프**: 대학별 합격률 비교

### 3. 보고서 생성
- **HTML 출력**: 웹 브라우저에서 확인 가능한 보고서
- **반응형 디자인**: 다양한 화면 크기에 최적화
- **목차 기능**: 대학별, 전형별 빠른 네비게이션

## 🚀 설치 방법

### 필수 요구사항
- Python 3.8 이상
- pip (Python 패키지 관리자)

### 1. 저장소 클론
```bash
git clone https://github.com/username/susi_for_unitSchool.git
cd susi_for_unitSchool
```

### 2. 가상환경 생성 (권장)
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. 의존성 설치
```bash
pip install -r requirements.txt
```

만약 `requirements.txt` 파일이 없다면, 다음 패키지들을 직접 설치하세요:
```bash
pip install pandas openpyxl xlrd numpy plotly
```

## 💡 사용 방법

### 1. 프로그램 실행
```bash
python main.py
```

### 2. 데이터 파일 준비
- 엑셀 파일(.xlsx 또는 .xls)을 준비합니다
- 다음 컬럼들이 포함되어야 합니다:
  - F열: 지역
  - G열: 대학명
  - I열: 전형유형
  - K열: 전형명
  - M열: 모집단위
  - R열: 결과 (합격/불합격/충원합격)
  - AG열: 전교과등급
  - AH열: 환산등급

### 3. 데이터 로드 및 분석
1. **파일 선택**: "파일 찾아보기" 버튼으로 엑셀 파일 선택
2. **데이터 로드**: "데이터 로드" 버튼 클릭
3. **필터 설정**: 원하는 조건을 다중 선택
4. **보고서 생성**: "HTML 보고서 생성" 버튼 클릭

### 4. 결과 확인
- `output_htmls` 폴더에 HTML 파일이 생성됩니다
- 웹 브라우저에서 파일을 열어 결과를 확인할 수 있습니다

## 📁 파일 구조

```
susi_for_unitSchool/
├── main.py                 # 메인 GUI 애플리케이션
├── data_processor.py       # 데이터 처리 및 통계 계산
├── html_generator.py       # HTML 보고서 생성
├── filter_widgets.py       # 필터 UI 컴포넌트
├── utils.py                # 유틸리티 함수
├── config.py              # 설정 파일
├── README.md              # 프로젝트 문서
├── requirements.txt       # Python 의존성
└── output_htmls/          # 생성된 HTML 보고서
    └── 선택된_모집단위_입시결과.html
```

### 주요 모듈 설명

#### `main.py`
- Tkinter 기반 메인 GUI 애플리케이션
- 파일 로드, 필터링, 보고서 생성 기능 제공

#### `data_processor.py`
- 엑셀 파일 읽기 및 전처리
- 통계 계산 (평균, 표준편차, 합격률 등)
- JSON 인코딩 지원

#### `html_generator.py`
- Plotly 기반 인터랙티브 차트 생성
- HTML 보고서 템플릿 생성
- CSS 스타일링 및 JavaScript 구현

#### `filter_widgets.py`
- 다중 선택 필터 UI 컴포넌트
- 검색 기능 및 실시간 필터링 지원

#### `config.py`
- 모든 설정값과 상수 중앙 관리
- 색상, 레이아웃, 파일 경로 등 설정

## ⚙️ 설정 방법

### 1. 기본 설정 변경
`config.py` 파일에서 다음 설정들을 수정할 수 있습니다:

```python
# 출력 디렉터리 변경
DEFAULT_OUTPUT_DIR = Path("my_output")

# 차트 색상 변경
CHART_COLORS = {
    "합격": {"border": "#Custom_Color", ...},
    # ...
}

# 윈도우 크기 변경
MAIN_WINDOW = {
    "geometry": "1200x800",
    # ...
}
```

### 2. 엑셀 컬럼 매핑 변경
데이터 파일의 컬럼 위치가 다른 경우:

```python
EXCEL_COLUMNS = {
    "region": "A",      # F열 → A열로 변경
    "univ": "B",        # G열 → B열로 변경
    # ...
}
```

### 3. 디버그 모드 활성화
```python
DEBUG_MODE = True  # 상세 로그 출력
```

## 🔧 문제 해결

### 자주 발생하는 문제들

#### 1. "모듈을 찾을 수 없습니다" 오류
```bash
# 해결방법: 의존성 재설치
pip install -r requirements.txt
```

#### 2. 엑셀 파일 로드 실패
- 파일이 다른 프로그램에서 열려있지 않은지 확인
- 파일 경로에 한글이나 특수문자가 없는지 확인
- 엑셀 파일 형식이 `.xlsx` 또는 `.xls`인지 확인

#### 3. HTML 보고서가 생성되지 않음
- `output_htmls` 폴더 쓰기 권한 확인
- 디스크 용량 확인
- 인터넷 연결 확인 (Plotly CDN 접속용)

#### 4. 차트가 표시되지 않음
- 인터넷 연결 확인 (Plotly CDN)
- 웹 브라우저의 JavaScript 활성화 확인

### 로그 확인 방법
```python
# config.py에서 디버그 모드 활성화
DEBUG_MODE = True

# 또는 직접 로그 출력
python main.py --debug
```

## 📈 성능 최적화 팁

### 1. 대용량 파일 처리
- 50MB 이상의 엑셀 파일은 처리 시간이 오래 걸릴 수 있습니다
- 필요한 데이터만 포함된 파일을 사용하세요

### 2. 메모리 사용량 최적화
- 불필요한 컬럼 데이터는 제거하세요
- 프로그램 사용 후 메모리 정리를 위해 재시작하세요

### 3. HTML 보고서 최적화
- 너무 많은 데이터 포인트는 브라우저 성능을 저하시킬 수 있습니다
- 필터를 활용해 분석 범위를 적절히 제한하세요

## 🤝 기여하기

프로젝트 개선에 기여하고 싶으시다면:

1. Fork 이 저장소
2. Feature 브랜치 생성 (`git checkout -b feature/AmazingFeature`)
3. 변경사항 커밋 (`git commit -m 'Add some AmazingFeature'`)
4. 브랜치에 Push (`git push origin feature/AmazingFeature`)
5. Pull Request 생성

## 📞 지원 및 문의

- **개발팀**: 강원진학센터 입시분석팀
- **이메일**: [이메일 주소]
- **전화**: [전화번호]

## 📄 라이선스

이 프로젝트는 [MIT 라이선스](LICENSE) 하에 배포됩니다.

## 📝 업데이트 로그

### v1.0.0
- 초기 릴리스
- 기본 GUI 및 데이터 분석 기능
- HTML 보고서 생성 기능

---

**© 2025 강원진학센터 입시분석팀. All rights reserved.**

## 🌐 웹 버전(바닐라 JS) 사용 안내

Tkinter GUI 대신 브라우저에서 바로 엑셀을 올려 보고서를 확인할 수 있는 간이 웹 페이지를 제공합니다.

### 위치
- `web/index.html`

### 필요 환경
- 최신 브라우저 (Chrome/Edge/Safari 등)
- 인터넷 연결 (Plotly/SheetJS CDN 사용)  
  ※ 내부망에서는 CDN을 로컬 호스팅으로 바꿔야 합니다.

### 실행 방법
1. 터미널에서 웹 디렉터리로 이동  
   ```bash
   cd web
   ```
2. 간단한 정적 서버 실행 (예: Python)  
   ```bash
   python -m http.server 8000 --bind 127.0.0.1
   ```
3. 브라우저에서 접속  
   ```
   http://localhost:8000
   ```
4. `index.html` 화면에서 엑셀을 업로드하고 “보고서 생성” 클릭.

### 지원 데이터 형식
- 컬럼 위치: F(region), G(univ), I(apptype), K(subtype), M(dept), R(result), AG(all_subj_grade), AH(conv_grade)
- 상단 2행은 건너뜁니다.

### 주요 기능 (웹)
- 전체 데이터 요약, 전형유형별/등급대별 시각화, 상위 20개 대학 합/충원/불합격 스택 막대
- 대학별 → 전형유형별/세부유형별/모집단위별 통계 및 산점도
- 전교과/환산 등급 토글, 목차 네비게이션
