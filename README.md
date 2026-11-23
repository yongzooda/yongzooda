<div align="center">

# 이용주

### 확인되지 않은 부분을 그냥 넘기지 못하는 백엔드 개발자

<sub>Java · Spring Boot&nbsp;&nbsp;|&nbsp;&nbsp;컴퓨터공학 전공, 2027년 2월 졸업 예정&nbsp;&nbsp;|&nbsp;&nbsp;멋쟁이사자처럼 백엔드 부트캠프 15기 수료</sub>

<a href="#projects">프로젝트</a> · <a href="#skills">기술</a> · <a href="#awards">수상</a> · <a href="#education">학력과 자격증</a>

</div>

<br>

## 🙋 About Me

- Java·Spring Boot로 서버를 만드는 신입 백엔드 개발자
- 졸업 프로젝트와 공모전에서 서비스를 처음부터 만들어 배포와 운영까지 경험 (공모전 수상 3회)

**일할 때 지키는 것**

- **원인이 분명해질 때까지 확인** · 증상이 사라졌다고 끝내지 않고, 고친 뒤에는 수정을 되돌려 테스트가 실패하는지까지 확인
- **확인한 것은 기록으로** · 고친 이유는 PR에, 팀이 따라야 할 절차는 안내 문서로 정리
- **AI의 답도 근거가 있을 때만** · 규칙으로 정할 수 있는 판단은 규칙에 맡기고, 근거가 모자라거나 형식이 어긋난 답은 버림

**만들고 싶은 것** · AI가 내린 판단도 받아 본 사람이 이유를 납득할 수 있는 서비스

<br>

<a id="projects"></a>

## 🚀 Projects

| 프로젝트 | 서비스 | 담당 | 기간 |
| :-- | :-- | :-- | :-- |
| [**CoreMate**](#coremate) | CS 전공지식 반복 학습 앱 · 졸업 프로젝트 | AI · 백엔드 · 인프라 | 2026.05 ~ 11 |
| [**TourLint**](#tourlint) | 여행상품 일정 검수 서비스 · 장려상 | 백엔드 · 화면 · 배포와 운영 | 2026.08 ~ 09 |
| [**AmbuDock**](#ambudock) | 응급실 추천 웹 서비스 · 은상 | 기획 · 백엔드 · 화면 · 발표 | 2025.10 ~ 11 |
| [**FinProof**](#finproof) | 금융 광고 심의 AI 에이전트 · 대상 | 사회맥락 리스크 검토 · AI 분석 속도 개선 | 2026.05 ~ 07 |

<sub>프로젝트마다 트러블슈팅과 기술 선택 이유를 정리한 상세 문서는 각 프로젝트 아래 링크에서 볼 수 있음</sub>

<a id="coremate"></a>

### CoreMate · CS 전공지식 반복 학습 앱

<sub>졸업 프로젝트 · 2026.05 ~ 11 · <a href="https://github.com/seoultech-cse-capstone/coremate">GitHub</a> · <a href="https://github.com/yongzooda/yongzooda/blob/main/projects/coremate.md">상세 문서</a></sub>

CS 전공 문제를 풀면 틀린 문제, 오래 걸린 문제, 힌트를 쓴 문제를 모아 약점 분석표를 만들어 주는 모바일 학습 앱. 2026년 9월 AWS에 배포해 운영을 시작하고 App Store에 출시

**주요 기능**

- 자료구조·알고리즘·운영체제·데이터베이스·컴퓨터구조·네트워크 문제 풀이와 단원별 모의고사
- 풀이 기록으로 약점 개념과 원인을 짚어 주는 AI 약점 분석표
- 문제를 풀어 모은 경험치와 코인으로 아바타와 방 꾸미기, 친구와 알림

**담당 업무** · AI · 백엔드 · 인프라

- **AI 학습 콘텐츠 파이프라인** <sub>Python · LangChain · LangGraph</sub>
  - 무료로 공개된 전공 교재와 기술 문서 16종을 근거로 개념 카드, 오개념, 문항, 검수 결과를 만드는 11단계 파이프라인
  - 6과목 문항 3,283개 생성, 생성·검수 모델은 Gemini와 GPT 계열을 비교해 선정
  - 터미널에서 돌리던 스크립트를 내부용 FastAPI 서버로 옮기고, 사람이 승인한 문항만 서비스 DB에 반영
- **AI 약점 분석** <sub>Spring Boot · FastAPI · OpenAI</sub>
  - 오답률, 오래 걸린 비율, 힌트 비율로 개념별 약점 점수를 매기는 서버 로직
  - 서버가 고른 후보 3개까지만 AI가 유형과 원인을 해석하는 분석 API, 근거가 모자라면 AI를 부르지 않음
  - 진단과 복습 팁이 먼저 보이도록 분석표의 서버 응답과 화면 개편
- **서버 API** <sub>Spring Boot · JPA · MySQL</sub>
  - 보상·레벨·아바타·내 방·친구·알림 API
  - 광고 시청 보상은 구글이 보내는 서명 콜백(AdMob SSV)을 검증한 뒤에만 지급
  - 기기별 로그인 세션, 회원 탈퇴 시 개인정보 삭제와 카카오·Apple 연결 해제
- **앱 화면** <sub>React Native</sub>
  - 친구, 알림, 광고 화면
- **인프라와 출시** <sub>AWS · GitHub Actions</sub>
  - AWS ECS Fargate 운영 환경 구성 (ECR, RDS, CloudFront, Parameter Store)
  - main에 머지하면 이미지를 빌드해 ECS에 배포하는 GitHub Actions 워크플로와 배포 런북
  - Flyway 도입, 운영 DB 변경을 마이그레이션 파일로 관리
  - App Store 출시, Google Play 출시 준비

**트러블슈팅**

- [날짜가 바뀐 뒤 첫 요청끼리 부딪히던 데드락](https://github.com/yongzooda/yongzooda/blob/main/projects/coremate.md#deadlock)
- [검토 없이 바뀌던 운영 DB를 Flyway로 전환](https://github.com/yongzooda/yongzooda/blob/main/projects/coremate.md#flyway)
- [16일 동안 조용히 실패하던 완성 알림](https://github.com/yongzooda/yongzooda/blob/main/projects/coremate.md#notification)

`Java 21` `Spring Boot 4` `JPA` `MySQL 8.4` `Redis` `Flyway` `Python` `FastAPI` `OpenAI` `AWS ECS` `React Native`

<br>

<a id="tourlint"></a>

### TourLint · 여행상품 일정 검수 서비스

<sub>2026 관광데이터 활용 공모전 장려상 · 2026.08 ~ 09 · <a href="https://github.com/tourlint/tourlint">GitHub</a> · <a href="https://tourlint-web.up.railway.app">서비스</a> · <a href="https://github.com/yongzooda/yongzooda/blob/main/projects/tourlint.md">상세 문서</a></sub>

여행상품 일정표를 한국관광공사 관광정보와 대조해, 휴관일에 잡힌 방문이나 끝난 행사, 모자란 이동 시간 같은 문제를 출시 전에 근거와 함께 짚어 주는 검수 웹 서비스

**주요 기능**

- 쉬는 날과 운영시간, 행사 기간, 이동 시간, 날씨 등 규칙 10가지로 일정 검수
- 문제마다 관광공사 원문과 판정 근거, 고칠 수 있는 수정안 표시
- 등급별 건수로 출시 준비도 점수 계산, 출시한 뒤 관광정보가 바뀌면 알림

**담당 업무** · 백엔드 · 화면 · 배포와 운영

- **검수 엔진** <sub>NestJS · PostgreSQL</sub>
  - 검수 규칙 10가지와 네 등급 판정(차단·오류·주의·확인 불가), 출시 준비도 점수 계산
  - 외부 API와 DB에 기대지 않는 순수 함수 구조, 엔진이 외부 코드를 가져오면 eslint에서 막도록 설정
  - 관광지 운영시간과 휴무일 문장을 구조로 바꾸는 규칙 파서, 파서가 못 읽은 조각만 LLM으로 보완
- **외부 API 연동**
  - 한국관광공사 TourAPI, 카카오모빌리티 길찾기, 기상청 예보 연동
  - 오류 종류별 재시도와 서비스 전체 하루 호출 예산 관리
  - 출시한 상품의 관광정보 변경을 찾는 변경 감지 배치, 검수 리포트 PDF 출력
- **보안**
  - 요청마다 소유권을 확인하는 접근 통제, 로그인 실패 잠금, 요청 횟수 제한
- **화면** <sub>Next.js</sub>
  - 검수 근거 화면(관광공사 원문, AI 해석, TourLint 판정)을 비롯한 웹 화면 작업
  - API와 화면이 같은 타입을 쓰는 공용 패키지
- **CI와 배포** <sub>GitHub Actions · Railway</sub>
  - 빌드, 린트, 타입 검사, 실제 PostgreSQL 테스트, 저장소 전체 비밀키 검사를 돌리는 CI
  - Railway 배포, 새 버전이 실제로 올라왔는지 확인하고 실패하면 다시 띄우는 워크플로
  - 관광공사 API에 실제로 닿아야 정상으로 답하는 헬스체크
  - 심사위원이 서비스를 직접 써 보는 1차 심사용 체험 안내서

**트러블슈팅**

- [외부 API에 못 닿는 서버가 배포 검사를 통과한 장애](https://github.com/yongzooda/yongzooda/blob/main/projects/tourlint.md#healthcheck)
- [첫 수정이 문제를 옮기기만 한 검수 점수 오류](https://github.com/yongzooda/yongzooda/blob/main/projects/tourlint.md#score)
- [되돌려도 통과하던 테스트와 그 뒤 만든 검증 규칙](https://github.com/yongzooda/yongzooda/blob/main/projects/tourlint.md#guard)

`TypeScript` `NestJS` `PostgreSQL` `Next.js` `GitHub Actions` `Railway` `Claude API`

<br>

<a id="ambudock"></a>

### AmbuDock · 응급실 추천 웹 서비스

<sub>디지털 사회혁신 서비스 개발·아이디어 공모전 은상 · 개인 프로젝트 · 2025.10 ~ 11 · <a href="https://github.com/yongzooda/AmbuDock">GitHub</a> · <a href="https://github.com/yongzooda/yongzooda/blob/main/projects/ambudock.md">상세 문서</a></sub>

실시간 응급실 병상 정보에 재난문자와 이동 시간까지 따져, 지금 갈 만한 응급실을 골라 주는 모바일 웹 서비스

**주요 기능**

- 지도에서 주변 응급실의 실시간 가용 병상 확인
- 병상 혼잡도와 재난문자, 이동 시간을 따져 갈 만한 응급실 추천
- 고른 병원으로 TMAP 길안내 연결

**담당 업무** · 기획 · 백엔드 · 화면 · 발표

- **기획과 발표**
  - 「공공은 판단의 근거, 민간은 실효성」을 원칙으로 서비스 기획, 상세기획서 작성과 본선 발표
- **데이터 수집** <sub>Spring Boot · MySQL · Flyway</sub>
  - 국립중앙의료원 응급실·중환자실 병상(60초)과 행정안전부 재난문자(3분)를 모으는 스케줄러
  - 처음 보는 병원은 카카오 로컬 API로 좌표와 행정구역을 찾아 자동 등록
  - 재난문자 심각도를 DB 키워드 규칙으로 판정하고, 수신 지역을 행정구역과 연결
- **추천 API**
  - 가용 병상으로 병원별 혼잡 점수를 매기고 중환자실 여유로 보정, 5분 넘은 정보는 감점하고 1시간 넘으면 제외
  - 재난문자 심각도에 따라 후보에서 빼거나 경고 배지 표시
  - TMAP으로 차량·도보 이동 시간 계산, 실패하거나 1.5초를 넘기면 직선거리로 추정
  - 추천할 때마다 계산 근거를 기록, 탐색 반경 같은 기준값은 DB 설정과 관리자 API로 변경
- **화면** <sub>React · TypeScript</sub>
  - 휴대폰에 맞춘 카카오 지도 화면 (병원 마커와 실시간 가용 병상)
  - 병원을 고르면 TMAP 앱 길안내로 연결, 앱이 없으면 설치 화면으로 이동

**트러블슈팅**

- [응급실 공공데이터가 들어오지 않던 문제](https://github.com/yongzooda/yongzooda/blob/main/projects/ambudock.md#encoding)
- [캐시를 붙였는데도 잦던 TMAP 호출](https://github.com/yongzooda/yongzooda/blob/main/projects/ambudock.md#cache)

`Java 21` `Spring Boot 3.5` `JPA` `MySQL` `Flyway` `Caffeine` `React` `TypeScript`

<br>

<a id="finproof"></a>

### FinProof · 금융 광고 심의 AI 에이전트

<sub>JB금융그룹 Fin:AI Challenge 대상 · 2026.05 ~ 07 · <a href="https://github.com/jb-finproof-team/FinProof">GitHub</a> · <a href="https://github.com/yongzooda/yongzooda/blob/main/projects/finproof.md">상세 문서</a></sub>

금융 홍보물을 올리면 AI가 글자를 읽고 법령, 사내 심의기준, 과거 심의 사례에서 근거를 찾아 위험한 표현과 수정 의견 초안을 먼저 정리해 주는 준법심의 에이전트

**주요 기능**

- 홍보물·약관·상품설명서를 한 번에 올리면 OCR로 읽고 위험한 표현과 근거 표시
- 표현, 상품, 법규, 사내 기준, 과거 사례, 사회맥락을 맡은 AI 에이전트가 함께 검토
- 심의 요청부터 준법심의자의 최종 판단, 심의필 발급까지 한 플랫폼에서 처리

**담당 업무** · 사회맥락 리스크 검토 · AI 분석 속도 개선

- **사회맥락 리스크 에이전트**
  - 법에 걸리지 않아도 게시 시기나 표현 때문에 논란이 될 광고를 짚는 에이전트를 분석 파이프라인에 추가
  - DB 마이그레이션(Prisma), 프롬프트, 모델 라우팅, 심의 화면 배지까지 연결
  - 근거 검색에 캠페인명과 게시 예정일 같은 요청 정보 반영, OCR이 글자를 못 읽으면 요청서 내용으로 분석 진행
- **사회맥락 규칙 엔진**
  - 민감한 사건의 날짜와 표현을 이어 둔 지식 그래프 데이터를 읽어, 게시 예정일과 문구가 걸리는지 판정하는 엔진
  - 걸린 날짜·사건·표현·규칙을 근거로 붙이고, 위험 판정도 반려 대신 보류로 넘겨 심의자가 결정
  - 민감한 날짜와 표현이 겹치는 광고, 추모처럼 예외로 둘 문맥을 테스트 케이스로 작성
- **AI 분석 속도 개선**
  - 에이전트마다 우선순위가 높은 이슈 3개까지만 넘기고, 가벼운 검토는 Claude Haiku, 법규와 종합 판단은 Claude Sonnet에 배분
  - 3분 넘게 걸리던 분석을 3분 안으로 단축, 심의 대기 화면의 3분 제한 제거
- **제품 브리프**
  - 대회 자료를 개발 기준으로 다시 정리한 제품 브리프와 기능 문서 작성

**트러블슈팅**

- [AI가 확정하지 못하던 사회맥락 판단을 규칙 엔진으로](https://github.com/yongzooda/yongzooda/blob/main/projects/finproof.md#rule-engine)
- [3분을 넘기던 AI 분석 시간 줄이기](https://github.com/yongzooda/yongzooda/blob/main/projects/finproof.md#speed)

`Next.js` `TypeScript` `PostgreSQL` `pgvector` `Prisma` `Claude API`

<br>

<a id="skills"></a>

## 🛠 Tech Stack

| 분야 | 기술 | 써 본 곳 |
| :-- | :-- | :-- |
| **Java** | ![Java](https://img.shields.io/badge/Java-007396?style=flat-square&logo=openjdk&logoColor=white) ![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white) ![JPA](https://img.shields.io/badge/JPA-59666C?style=flat-square&logo=hibernate&logoColor=white) ![Spring Security](https://img.shields.io/badge/Spring%20Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white) | CoreMate와 AmbuDock 백엔드, 부트캠프 팀 프로젝트 |
| **TypeScript** | ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white) ![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white) ![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white) | TourLint 백엔드와 화면, FinProof |
| **Python** | ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white) ![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white) | CoreMate AI 서버와 문항 생성 파이프라인 |
| **Database** | ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white) ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white) ![Redis](https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white) ![Flyway](https://img.shields.io/badge/Flyway-CC0200?style=flat-square&logo=flyway&logoColor=white) | CoreMate(MySQL·Redis·Flyway), AmbuDock(MySQL·Flyway), TourLint와 FinProof(PostgreSQL) |
| **Infra** | ![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square) ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white) ![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white) ![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=flat-square&logo=railway&logoColor=white) | CoreMate AWS ECS 배포, TourLint Railway 배포와 CI |
| **AI** | ![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square) ![Claude](https://img.shields.io/badge/Claude-D97757?style=flat-square&logo=claude&logoColor=white) ![Gemini](https://img.shields.io/badge/Gemini-8E75B2?style=flat-square&logo=googlegemini&logoColor=white) | CoreMate 문항 생성과 약점 분석, TourLint 운영시간 해석, FinProof 심의 에이전트 |
| **Frontend** | ![React](https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black) ![React Native](https://img.shields.io/badge/React%20Native-61DAFB?style=flat-square&logo=react&logoColor=black) | AmbuDock 지도 화면, CoreMate 친구·알림·광고 화면 |

<br>

<a id="awards"></a>

## 🏆 Awards

| 수상 | 대회 | 프로젝트 | 시기 |
| :-- | :-- | :-- | :-- |
| 🥇 **대상** | JB금융그룹 Fin:AI Challenge<br><sub>JB금융그룹 · AI Agent 서비스 개발 과제</sub> | FinProof | 2026.07 |
| 🥈 **은상** | 2025 민관협력 지원 플랫폼 활용 디지털 사회혁신 서비스 개발·아이디어 공모전<br><sub>과학기술정보통신부 · 한국지능정보사회진흥원 · 서비스 개발 부문</sub> | AmbuDock | 2025.12 |
| 🏅 **장려상** | 2026 관광데이터 활용 공모전<br><sub>한국관광공사 · 웹·앱 구현 부문</sub> | TourLint | 2026.11 |

<br>

<a id="education"></a>

## 🎓 Education & Certificates

| 기간 | 내용 |
| :-- | :-- |
| 2020.03&nbsp;~&nbsp;2027.02 | 컴퓨터공학 전공 (졸업 예정) · 학점 3.98 / 4.5 |
| 2025.02&nbsp;~&nbsp;2025.08 | 멋쟁이사자처럼 백엔드 자바 부트캠프 15기 수료 (960시간)<br><sub>Java 기초부터 Spring Boot, JPA, Spring Security까지 학습하고 팀 프로젝트로 구현, 후반 수업에서 Docker와 Kubernetes 학습</sub> |

| 자격증 | 발급 기관 | 취득 |
| :-- | :-- | :-- |
| 정보처리기사 | 한국산업인력공단 | 2026.09 |
| SQLD | 한국데이터산업진흥원 | 2024.12 |
| ADsP | 한국데이터산업진흥원 | 2024.11 |
