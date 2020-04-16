---
title: 자기소개서
category:
  - 경력
last_modified_at: 2020-04-16
---
> code : 훌륭한 코드는 훌륭한 문서보다 낫다 - Steve McConnell (개발자)

--------

### '열심인(Eager)' 개발자입니다.

현 재직 중인 직장에서 데이터 수집 파트부터 migration 및 service를 담당하고 있습니다.

목표는 항상 열심인(Eager) 개발자가 되어 후배개발자들이 목표로 삼는 SW를 만드는 것이 목표입니다.

책을 통해 지식을 주로 습득하며 , 프로젝트시 당장 돌아가는 서비스보단 관리 유지보수가 편한 서비스로 만들려고 노력합니다.

TDD 기반 소프트웨어 설계를 지향하고, MS 아키텍쳐에 관심있으며 , 주석과 템플릿 , test유닛을 활용한 유지보수 관리를 중요시 합니다.


### 개발문화 만들기

개발자는 혼자하는게 아니라 팀원들의 소통 , 협업이 중요하다고 생각하고 그러한 사람이 되기 위해 노력하고 행동합니다.

이팝콘 회사에 10개월차쯤 되었을 때 선임 개발자분이 퇴사하셨습니다.

그로인해 경력직 인원이 부족하여 BI팀 팀장역할을 맡게 되었습니다.

부담이 많이 됬지만 어떻게든 잘 꾸려가자라는 생각으로 스타트업이라 갖춰지지 않았던 코드리뷰 , 일일 기술(업무)회의 , 스터디 등 도입하여 

다니는 팀원들에게 만족감과 성취감을 줌과 동시에 좋은 개발문화를 위해 노력했습니다.

지금은 완전히 팀 문화로 자리잡았고 , 기술이슈나 스킬이슈 등 이슈사항이 있을 때 모든 팀원이 다같이 고민할 수 있는 환경을 만들었습니다.

현재는 R&T 시스템을 도입 하였습니다.

R&T 란 read & Technology Sharing 의 약자로써 주에 1번 2시간을 스터디룸을 빌려서 각자 현재 공부하고 있는 IT서적을 읽은 후

책을 통해 각자 얻은 지식을 공유함으로써 팀원들의 지식을 향상 시키고

다양한 서적들의 내용들을 공유함으로써 IT에 대한 전반적인 시야를 넓히기 위한 프로그램입니다.

팀원들의 반응이 좋고 실제로 개발자들과의 소통함에 있어서 많은 도움이 되었다는 피드백을 받았습니다.

### 업무중 기억에 남는 코드

```
if (resultList.size() >= detailChunkSize || (itemUrlSize == seq.get()) || debug) {
	for (Future<Item> f : resultList) {
		if (f != null) {
			Item item = null;
			try {
				TimeUnit unit =(slowItemAlreadyYn) ? TimeUnit.MILLISECONDS :TimeUnit.SECONDS;
				item = f.get(CoupangCV.DETAIL_TIME_OUT, unit);
			} catch (TimeoutException e1) {
				slowItemHandler.push(this, f);
				slowItemAlreadyYn = true;
				logger.error(getClass().getSimpleName(), "TimeoutException", f.toString());
			} catch (InterruptedException | ExecutionException e2) {
				logger.error(getClass().getSimpleName(), "Getting Future Item is failed", e2);
			}
			if (item != null) {
				itemList.add(item);
			}
		}
	}
	resultList.clear();
}
```

위 코드는 비지니스 로직 중 한부분입니다.

해당 코드는 callable 블락 비동기 형태의 코드로 수집업무 진행하던 중..

http 통신과정에 기존에 생각했던 청크단위의 업무속도가 나오지않아 스케쥴링했던 시간이 오버해드가 나오던 상황이였습니다.

그것을 해결했던 비지니스로직 알고리즘입니다.

핵심적인 부분은 future<> 에서 get 으로 response 를 기다리는 것에 시간제한을 둬서 제한시간 이상 걸리는 쓰레드는

새로만든 queue 에 넣어서 따로 처리하도록 처리한 로직입니다.

해당 알고리즘 적용 후 여러개의 프로세스로 처리하던 수집업무를 한개의 프로세스로 완료할 수 있게끔 만든 로직입니다.

업무처리중 가장 기억에 남는 코드입니다.
