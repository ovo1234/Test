# 개념
 - commit(커밋) : 세이브에 해당하는 단어, 저장 시점으로 돌아갈 수 있음. 저장을 원하는 파일들을 묶어서 커밋 명령 수행하면 됨
 - add(스테이지에 올린다) : 저장을 원하는 파일들을 묶는 일, 스테이지에 파일을 올린다.
 - push(github에 업로드) : commit한 내용이 컴퓨터에 저장되며 업로드 됨.

# 소스트리 사용하여 push하기
- 저장소(repository) 생성 -> clone에 저장소를 복사해오기(저장소 주소) -> 스테이지에 파일 추가 -> 모두 스테이지에 올리기 -> 커밋하기 -> push
 > 이때 커밋 메시지 작성 시 첫 줄에 간단 명확하게 내용을 쓴 후 한 줄 비우고 자세한 내용작성
 > push할 때, 오류 발생시 토큰 생성 후 설정에 들어가 주소 변경
    > 주소 <토큰>@ 주소
 > 커밋 메시지는 이 파일을 commit 할 때 어떤 행동을 했는가를 보여줌 -> 협력할 때 그 내용을 가지고 좀 더 빠르게 확인 가능함.

# 변경사항 취소하기
 만일 push 후 에디터에서 내용 변경 후 저장을 하면 스테이지에 파일이 올라감.
 그곳에서 코드뭉치 버리기 기능을 사용하면 변경사항을 되돌릴 수 있음.
  > checkout을 사용하여 마지막 커밋으로 돌아갈 수 있음.

파일 push 후 내용 변경 시 그냥 똑같이 커밋 후 푸쉬하면 내용이 변경되어있음.

# 브랜치의 개념
 - 브랜치 : 기능 변경을 하고 싶을 때 생성 및 사용
   가상의 브랜치, 하나의 브랜치로 특정한 부분으로 돌아가고 싶을때 사용함(가지)
   깃에서는 한 번에 하나의 브랜치에서만 작업이 가능하여 헤드 브랜치라고도 부름
 - 머지(merge) : 한 브랜치의 내용을 다른 브랜치에 반영
 - 체크아웃(checkout) : 저장소에서 특정 커밋이나 브랜치로 돌아가고 싶을 때 사용
 > 최종본은 무조건 master(main)에 있어야하며 수정본은 브랜치를 사용하여 해야함.

 > 커밋되어있는 상태에서 브랜치 생성할 위치를 결정 후 브랜치 생성 -> 브랜치를 변경하기 위해서는 체크아웃을 하면됨(소스트리에서는 더블클릭 하면 됨.)

 ## 병합(merge) 살펴보기
  - 병합이란? 하나의 브랜치를 현재 브랜치(head)와 합치는 것을 병합이라고 한다.
  > 헤드 브랜치에 변경사항이 없을 경우 : 잘 병합이 된다.
  > 가지가 생겨난 경우 : 과거의 커밋으로부터 브랜치를 생성하거나, 다른 커밋이 있거나 여러 브랜치를 동시에 작업하면서 병합을 시도할 경우 충돌이 일어날 수 있음

  ## 충돌 해결하기
   - 충돌은 자동병합 실패시 발생
   - 안쓰는 브랜치 삭제하기
   - 충돌의 발생원인
    > 자동병합 실패, 같은 파일을 두 커밋이 편집했을 경우
    > 에디터 이용, 병합툴 이용, 소스트리 이용

## 이전 커밋으로 되돌리기
- reset 사용하기
 > 이 브랜치까지 되돌리기 -> hard 모든 작업 버림 : 선택된 이후 커밋이 다 날라감 \
 > git reset --hard 로 커밋을 되돌리기 

- 새로운 브랜치 만들어서 사용하기 
 > 되돌릴 커밋 대상으로 브랜치 만들어서 사용함.

- revert 사용하기
 > 대상 커밋을 head 커밋의 자식으로 새로 생성한다.
 > revert 대상 커밋은 사라지지 않는다. 되돌린 새로운 커밋이 생겨난다.
 > 이전 커밋 기록이 다 남아 있다. / 충돌 날 가능성이 매우 높다.

- revert 여러 커밋 되돌리기
 > 최신부터 순서대로 revert를 반복 적용하면 됩니다.


## 브랜치와 스태시
 - 브랜치

 - 스태시 : 임시 저장 공간에 현재 작업 내용이 저장됨. 언제든지 다시 복구 가능함.
  : 다른 브랜치로 체크 아웃하기 전에 현재 작업 내용을 저장하는 임시 저장소
 > 커밋 덮어쓰기 (commit --amend) : 커밋 그대로 하고 직전 커밋 내용 정정을 눌러 커밋 덮어쓰기

 ## rebase로 병합학기
 - 리베이스 : 병합과 마찬가지고 두 브랜치의 내용을 하나로 합치고 싶을 때 사용(머지와 달리 트리가 깔끔하게 유지됨)
  > 원격 저장소에 올라간 경우 + 협업을 하고 있는 경우 위험함.