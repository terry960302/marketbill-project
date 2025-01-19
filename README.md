<div align="right">
<b> Contributor : Taewan Kim(100%)</b>
</div>

<br/>

# marketbill-project(BACKEND)
<div align="center">
  <section>
    <img src="https://github.com/user-attachments/assets/d713f402-220d-49b6-aaa9-a989857938a1" width="115" alt="두 번째 이미지"/>
    <img src="https://github.com/user-attachments/assets/b294c293-3ac4-4e8a-b8f7-fb801ae56a06" width="600" alt="첫 번째 이미지"/>
  </section>
</div>

# 📌 About This Project

### 내 손 안의 꽃 시장을 만들어요.

마켓빌은 꽃 시장에서 이뤄지는 일련의 활동을 온라인으로 전환하는 것을 목표로 해요. 꽃 시장에서 꽃집 사장님이 하는 주요 활동은 **상품 탐색, 주문, 배송 및 픽업, 거래 증빙** 4가지로 요약돼요.

**전산화가 잘 되어 있지 않아 주요 활동 4가지에서 꽃집 사장님은 모두 어려움을 겪고 있어요.** 시장에 직접 가지 않고서는 어떤 물건이 있는지, 얼마에 판매되는지 알 수 없어요. 그렇기 때문에 온라인으로 주문하는 것도 어려워요. 또한, 거래 기록이 전산에 남지 않기 때문에 영수증, 계산서 처리와 같은 거래 증빙도 어려워요.

**도매상도 꽃집 사장님의 주요 활동으로 인해 어려움을 겪고 있어요.** 오프라인에서 많은 고객을 응대하고, 전화로 오는 고객 문의까지 받다보니 정신이 없어요. 게다가 주문을 받을때 일일이 수기 영수증을 발급하다보니 추후에 거래 증빙 요청을 위한 서류 작업에도 많은 시간을 할애하고 있어요. 특히, 밤낮이 바뀐 새벽 시장에서 일을 하다보니 업무의 강도는 배가 되고 있어요. 

**마켓빌을 통해 꽃집 사장님은 지금보다 편리하게 꽃 거래를 할 수 있고, 도매상은 업무 강도를 낮출 수 있을 거에요.**

<br/>
<br/>

# 📌 Backend-Architecture

## What We Built
MarketBill의 백엔드는 4개의 독립적인 서비스로 구성되어 있습니다. 각 서비스는 특정 비즈니스 도메인에 집중하여 확장성과 유지보수성을 높였습니다.
서비스별 자세한 설명은 각 서비스별 저장소 README에 기재했습니다.

#### `Core GraphQL Server(Java/SpringBoot)`
중앙 API 서버로서 클라이언트의 모든 요청을 처리합니다. GraphQL을 도입하여 효율적인 데이터 요청과 응답을 구현했습니다.

#### `Receipt Processing Service(Python/FastAPI)`
- 핵심 비즈니스 로직인 영수증 PDF 처리를 담당
- 메인 API 서버에서 분리하여 시스템 부하 분산
- 대용량 PDF File I/O처리에 최적화된 독립 서비스

#### `Messaging Service(Golang/Echo)`
SMS 발송을 전담하는 독립 서비스로, 알림 시스템의 안정성과 확장성을 보장합니다.

#### `Scheduler Service(Golang/Echo)`
- 화훼 공식 사이트의 실시간 경매 정보 수집
- 정기적인 데이터 동기화 및 벌크 업로드 처리
- 외부 시스템과의 안정적인 데이터 통합 관리

## Tech Stack
- Language: Java 18.0.1.1, Python 3.8.3, Go 1.18.3
- Framework: Spring Boot 2.7.5, Netflix DGS(graphql), FastAPI,  
- Database: Postgresql
- Infrastructure: AWS(ECS, Lambda, CodeBuild, Code Pipeline, ECR, API gateway, Event Bridge)

## Key Features
- 소매상/도매상은 화훼 경매 데이터를 연동하여 실제 화훼 시장에서 거래되는 꽃정보 확인이 가능합니다.
- 소매상(플로리스트)는 도매상을 정하여 꽃에 대하여 '장바구니 > 주문'이 가능합니다.
- 도매상은 그날 들어온 주문을 합산하여 거래 명세서를 발급할 수 있습니다.
- 소매상은 도매상과 비즈니스 관계를 맺을 수 있습니다.

## CI/CD Pipeline(AWS)

### 배포 자동화 파이프라인 CD
<div align="center">
  <img src="https://github.com/user-attachments/assets/55ced4b9-2ce1-428c-8835-58b0b1d0b34f" 
       alt="배포 파이프라인" 
       width="800"/>
</div>

### 서버리스(Lambda) + API GW
<div align="center">
  <img src="https://github.com/user-attachments/assets/9320da46-d7af-4436-82b2-d5ef63971089" 
       alt="배포 파이프라인" 
       width="800"/>
</div>


