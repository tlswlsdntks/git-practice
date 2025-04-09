-- Git Bash에서 Git 전역 설정(사용자 이름, 이메일, 기본 브랜치)
$git config --global user.name 'xps13' ('', "" 둘다 사용가능)
$git config --global user.email 'tlswlsdntks@naver.com'
$git config --global init.defaultbranch main (기본 브랜치명는 master 이지만, 흑인-노예라는 편견 때문에 main을 권장함)


-- Git 설정 확인
$git config (--global) --list


-- 폴더를 생성하여, 에디터로 열기


-- 에디터 기본 설정 변경
ctrl + shift + p 눌러서 'select default profile' 검색해서 'Git Bash' 를 선택해준다.
ctrl + ` 눌러서 터미널을 열고,  우측 상단의 shell 기본 응용 프로그램을 'powershell' 에서 'bash' 로 변경해준다.


-- 에디터 아이콘 테마 변경
확장 프로그램에서 'Material Icon Theme' 를 검색하여 설치한다.


-- 깃 저장소 생성
$git init
깃 저장소를 생성하면 폴더 안에 .git 폴더가 생성된다.


-- 파일 생성하기(tigers.yaml, lions.yaml, secrets.yaml )
tigers.yaml 의 내용
team: Tigers

manager: John

members:
- Linda
- William
- David

lions.yaml 의 내용
team: Lions

manager: Mary

members:
- Thomas
- Karen
- Margaret

secrets.yaml 의 내용은 공란


-- 깃 상태 확인
$git status


-- .gitignore 생성
.gitignore 을 만들고 $git status 로 확인을 한다.
.gitignore 에 secrets.yaml 적고, 다시 $git status 를 확인해보자.

.gitigonre 의 작성 방법
# 주석
#

# 모든 file.c
file.c

# 최상위 폴더의 file.c
/file.c

# 모든 .c 확장자 파일
*.c

# .c 확장자지만 무시하지 않을 파일
!not_ignore_this.c

# logs란 이름의 파일 또는 폴더와 그 내용들
logs

# logs란 이름의 폴더와 그 내용들
logs/

# logs 폴더 바로 안의 debug.log와 .c 파일들
logs/debug.log
logs/*.c

# logs 폴더 바로 안, 또는 그 안의 다른 폴더(들) 안의 debug.log
logs/**/debug.log


-- 파일 하나를 로컬 저장소에 담기
$git add tigers.yaml


-- 모든 파일을 로컬 저장소에 담기
$git add .


-- 커밋
$git commit 
맨 처음 줄에 커밋 메세지를 적는다.
입력과 저장 순서는 i 를 눌러 커밋 메세지를 적고, ESC 를 누른 후 :wq 저장한다.


-- 커밋 메세지를 포함한 커밋
$git commit -m '커밋 메세지'


-- add + 커밋 메세지를 포함한 커밋 (새로 추가된(untracked) 파일이 없을 때 한정)
$git commit -am '커밋 메세지'

-- vi 명령어
입력 시작	i	명령어 입력 모드에서 텍스트 입력 모드로 전환
입력 종료	ESC	텍스트 입력 모드에서 명령어 입력 모드로 전환
저장 없이 종료	:q	
저장 없이 강제 종료	:q!	입력한 것이 있을 때 사용
저장하고 종료	:wq	입력한 것이 있을 때 사용
위로 스크롤	k	git log 등에서 내역이 길 때 사용
아래로 스크롤	j	git log 등에서 내역이 길 때 사용


-- 해당 브랜치의 깃 로그 확인
$git log


-- 변경 사항 테스트 해보기
lions.yaml 삭제
tigers.yaml 의 manager 를 Donald 로 변경
leopards.yaml 추가
leopards.yaml 의 내용
team: Leopards

manager: Luke

members:
- Linda
- William
- David

-- 깃 상태 확인
$git status

-- 파일의 수정 내용을 비교
$git diff

-- 파일을 로컬 저장소에 담기
$git add .

-- 커밋 메세지를 포함한 커밋
git commit -m "Replace Lions with Leopards"



-- 다음의 세 커밋들을 추가
🎯
tigers.yaml 의 members 에 - George 추가
커밋 메시지: Add George to Tigers

🎯
cheetas.yaml 추가

cheetas.yaml 의 내용
team: Cheetas
manager: Laura

members:
- Ryan
- Anna
- Justin
커밋 메시지: Add team Cheetas

🎯
cheetas.yaml 삭제
leopards.yaml 의 manager를 Nora 로 수정
panthers.yaml 추가
panthers.yaml 의 내용
team: Panthers

manager: Sebastian

members:
- Violet
- Stella
- Anthony
커밋 메시지: Replace Cheetas with Panthers


-- 실습 전 내역 백업
.git 폴더를 다른 폴더에 백업해보고, 기존 .git 폴더를 삭제해보고 깃이 작동하는 지 확인해본다.
확인 후, 원래대로 변경


-- 깃에서 과거로 돌아가는 두 방식
reset : 원하는 시점으로 돌아간 뒤 이후 히스토리를 지운다.
revert : 원하는 시점의 커밋을 거꾸로 실행합니다. (되돌리기: 추가 - 삭제, 삭제 - 추가)


-- reset 사용해서 과거로 돌아가기
$git log 를 확인하여 커밋 메세지 'Add team Cheetas' 의 커밋 해시를 복사한다.
$git reset --hard 커밋 해시 또는 $git reset --hard 간략한 커밋 해시
다시 한 번 'First Commit' 메세지 시점으로 돌아가 보기


-- reset 하기 전 시점으로 복원해보기
백업해둔 .git 폴더를 복구한다.
소스트리에서는 히스토리가 정상적으로 복구됐으나, 파일은 복구 이전 시점으로 확인할 수 있다.
$git reset --hard 
커밋 해시가 없다면 가장 마지막 커밋 시점을 자동으로 가리킨다.
커밋되지 않은 변경점을 확인하여 lions.yaml 삭제


-- revert 로 과거의 커밋 버전으로 되돌리기
$git log 를 확인하여 커밋 메세지 'Add George to Tigers' 의 커밋 해시를 복사한다.
$git revert 커밋 해시
revert 는 자동적으로 커밋 메세지가 적혀있으니, :wq 로 저장한다.


-- 'Replace Lions with Leopards' 의 커밋 되돌려보기
$git log 를 확인하여 커밋 메세지 'Replace Lions with Leopards' 의 커밋 해시를 복사한다.
$git revert 커밋 해시
'Replace Lions with Leopards' 의 커밋 내용
1. tigers.yaml 수정
2. leopards.yaml 추가
3. lions.yaml 삭제

이것을 revert 로 되돌려보면 
1. tigers.yaml 수정 전
2. leopards.yaml 삭제
3. lions.yaml 추가 이다.

그러나 'Replace Cheetas with Panthers' 시점의 커밋 내용 중 leopards.yaml 의 수정 내역이 존재한다.

즉, 커밋 내용끼리 충돌이 발생하여 충돌을 먼저 해결해야 한다.
-- 깃에서 충돌나는 leopards.yaml 을 삭제하는 것으로 결정
$git rm leopards.yaml
-- revert 를 계속 진행
$git revert --continue
-- 자동 커밋 메세지와 함께 저장
:wq


-- 'Replace Cheetas with Panthers' 의 커밋 시점으로 복원
$git reset --hard 커밋 해시


-- 커밋하지않고 revert 하기
$git revert --no-commit 커밋 해시 (revert 한 커밋 시점과 함께 다른 작업을 포함하여 커밋할 때 사용한다.)
작업 도중 다시 취소하려면 $git reset --hard


-- 소스트리로 과거의 커밋 버전 되돌리기
revert: RMB 를 누르고, '커밋 되돌리기'를 클릭
reset: RMB 를 누르고, '이 커밋까지 현재 브런치를 초기화'를 클릭하고, 'hard' 선택


-- 여러 브랜치 만들기
$git branch 브랜치 명


-- add-coach 란 이름의 브랜치 생성
$git branch add-coach


--브랜치 목록
$git branch


-- 브랜치 이동
$git switch 브랜치 명
과거에는 'checkout' 명령어를 사용하였는데, git 2.23 버전부터 'switch' 와 'restore' 로 분리되었다.


-- 브런치 생성과 동시에 이동
$git switch -c 브랜치 명
기존의 'git checkout -b 브랜치 명' 명령어가 'git switch -c 브랜치 명' 으로 변경되었다.


-- new-teams 란 이름의 브랜치를 생성과 동시에 이동
$git switch -c new-teams


-- 브랜치 삭제
$git branch -d 브랜치 명
다른 브랜치로 가져오지 않은 내용이 있는 브랜치를 지울 때는 -d 대신 -D(대문자) 로 강제 삭제해야 합니다.


-- to-delete 란 이름의 브랜치 만들고 삭제해보기
$git branch to-delete
$git branch -d to-delete


-- 브랜치 이름 바꾸기
$git branch -m 현재브랜치 명 바꿀 브랜치 명


-- 각각의 브랜치에서 서로 다른 작업해보기
⭐️ main 브랜치
🎯
leopards.yaml 의 members 에 - Olivia 추가
커밋 메시지: Add Olivia to Leopards

🎯
panthers.yaml 의 members 에 - Freddie 추가
커밋 메시지: Add Freddie to Panthers

⭐️ add-coach 브랜치
🎯
tigers.yaml 의 매니저 정보 아래 coach: Grace 추가
커밋 메시지: Add Coach Grace to Tigers

🎯
leopards.yaml 의 매니저 정보 아래 coach: Oscar 추가
커밋 메시지: Add Coach Oscar to Leopards

🎯
panthers.yaml 의 매니저 정보 아래 coach: Teddy 추가
커밋 메시지: Add Coach Teddy to Panthers

⭐️ new-teams 브랜치
🎯
pumas.yaml 추가
pumas.yaml 의 내용
team: Pumas

manager: Jude

members:
- Ezra
- Carter
- Finn
커밋 메시지: Add team Pumas

🎯
jaguars.yaml 추가
jaguars.yaml 의 내용
team: Jaguars

manager: Stanley

members:
- Caleb
- Harvey
- Myles
커밋 메시지: Add team Jaguars


-- 여러 브랜치 내역 보기 (소스트리와 유사)
$git log --all --decorate --oneline --graph


-- 브랜치 병합
merge 는 히스토리에 잔가지를 남기며, 이어붙인다. 주 브랜치는 메인 브랜치이다.
rebase 는 브랜치를 때어 메인 브랜치의 다음 커밋으로 이어붙인다. 주 브랜치는 때어질 브랜치이다.
(잔가지를 남기지 않아, 이미 공유된 커밋들에 대해서는 히스토리 파악이 힘드므로 rebase 를 사용하지 않는 것이 좋다.)


-- main 브랜치에 add-coach 브랜치를 merge
$git switch main
$git merge add-coach
:wq

merge 이후 병합된 브랜치 삭제
$git branch -d add-coach

-- merge는 reset 으로 되돌리기 가능
merge 하기 전 해당 브랜치의 마지막 시점으로 $git reset --hard 커밋 해시


-- new-teams 브랜치를 main 브랜치로 rebase
$git swtich new-teams
$git rebase main

소스트리에서 히스토리를 확인해보면 main 브랜치 시점이 뒤쳐져 있는 상황이다.
main 브랜치로 이동 후 new-teams의 시점으로 fast-forward 가 필요하다.
$git merge new-teams

rebase 이후 병합된 브랜치 삭제
$git branch -d new-teams


-- 병합 충돌 해결 상황 만들기
⭐️ conflict-1 브랜치, conflict-2 브랜치 생성

⭐️ main 브랜치
🎯	
tigers.yaml 의 manager 를 Kenneth 로 변경
leopards.yaml 의 coach 를 Nicholas 로 변경
panthers.yaml 의 coach 를 Shirley 로 변경
커밋 메시지: Edit Tigers, Leopards, Panthers

⭐️ conflict-1 브랜치
🎯
tigers.yaml 의 manager 를 Deborah 로 변경
커밋 메시지: Edit Tigers

⭐️ conflict-2 브랜치
🎯
leopards.yaml 의 coach 를 Melissa 로 변경
커밋 메시지: Edit Leopards

🎯
panthers.yaml 의 coach 를 Raymond 로 변경
커밋 메시지: Edit Panthers


-- main 브랜치에 conflict-1 브랜치 merge
$git switch main
$git merge conflict-1

해결 불가능 시, 
$git merge --abort 로 merge 를 중단

해결 가능 시, 해당 충돌 부분을 수정한 후
$git add .
$git commit 하면 commit 메세지가 자동부여된다.
:wq

merge 이후 병합된 브랜치 삭제
$git branch -d confilct-2


-- conflict-2 브랜치를 main 브랜치로 rebase 
$git switch conflict-2
$git reabase main

해결 불가능 시,
$git rebase --abort

해결 가능 시,
에디터에서 current 또는 incomming 을 선택하여 충돌을 해결하고,
$git add . 
$git rebase --continue
:wq 를 충돌 개수만큼 해줘야 한다.

소스트리에서 히스토리를 확인해보면 main 브랜치 시점이 뒤쳐져 있는 상황이다.
main 브랜치로 이동 후 conflict-2 의 시점으로 fast-forward 가 필요하다.
$git merge conflict-2

rebase 이후 병합된 브랜치 삭제
$git branch -d confilct-2


-- 깃 허브 토큰 발급
https://github.com/settings/tokens
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


-- 윈도우에 깃 허브 토큰 적용
8월 13일 부터 깃헙의 비밀번호 방식 인증이 사라지고, personal access token을 이용해야 한다.
자격 증명 관리 - windows 자격증명 - 일반 자격 증명 - 생성
주소: git:https://github.com
이름: tlswlsdntks
토큰: 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


-- 소스트리에 깃 허브 적용
도구 - 옵션 - 인증 에서 확인


-- 원격 저장소 다른 멤버와 공유
https://github.com/tlswlsdntks/git-practice/settings/access
레퍼지토리 - 세팅 - 엑세스 에서 멤버를 추가 한다.


-- 코드와 레퍼지토리 연동
https://github.com/tlswlsdntks/git-review
…or push an existing repository from the command line 이 부분을 복사하여 에디터 터미널에 붙여넣기 한다.
'error: failed to push some refs to' 에러가 표시되면 파일 하나를 생성하여,
$git add .
$git commit 을 해줘야 푸쉬할 목록이 생겨서 에러가 사라진다.

-- git remote add origin https://github.com/tlswlsdntks/git-practice.git : 깃에 원격 저장소를 추가한다.
원격 저장소: 깃 허브, 깃 랩, 비트 버킷 등 ..
origin 은 원격 저장소 이름이며 변경 가능하지만 보통 원격 저장소를 origin 이라고 한다.

-- git branch -M main : 메인 브랜치 이름을 main 으로 변경 한다.

-- git push -u origin main : origin 이라는 원격 저장소에 main 브랜치를 푸쉬하면서 동시에 추적(tracking) 브랜치로 설정하는 것이다.


-- 원격 저장소 확인
git remote (-v)


-- 타인의 프로젝트 다운로드 받기
https://github.com/tlswlsdntks/git-review
⭐️ download.zip 은 .git 폴더가 존재하지 않아, 협업 시에 사용하지 않는다.
⭐️ 새 폴더에 RMB 클릭 후, 추가 옵션 표시 - Open Git Bash here 선택
     git clone https://github.com/tlswlsdntks/git-practice.git 이런식으로 주소를 입력해주면 프로젝트가 생성된다.


-- 로컬 저장소 와 원격 저장소
로컬 저장소: 내 프로젝트 폴더 내에 .git 폴더가 존재하면 로컬 저장소이다.
원격 저장소: 내 깃 허브 계정의 레퍼지토리가 원격 저장소이다.


-- 원격 저장소로 커밋 밀어올리기 (푸쉬)
🎯
leopards.yaml 의 members 에 - Evie 추가
커밋 메시지: Add Evie to Leopards

소스트리를 확인해보면 origin/main (원격 저장소) 가 main (로컬 저장소) 보다 커밋 시점이 하나 낮게 있는 것을 알 수 있다.
$git push -u origin main 으로 대상 원격 브랜치를 사전에 지정해두었기 때문에 
$git push 로 원격 저장소에 커밋을 밀어올릴 수 있다.


-- 원격 저장소의 커밋 당겨오기 (풀)
깃 허브에서 수정을 한 작업은 원격 저장소에 푸쉬 한 것과 유사하다.
🌏
깃 허브에서 소스코드 - 연필 모양 - 커밋 메세지 입력
Leopards 의 members 에 - Dongho 추가
커밋 메시지: Add Dongho to Leopards

$git pull 을 한 후 소스트리를 확인해보면 origin/main (원격 저장소) 와 main (로컬 저장소) 의 시점이 맞는 것을 알 수 있다.
$git pull 의 디폴트는 merge 이다.


-- Pull 할 것이 있을 때 Push 를 하면? 이런 상황은 자동으로 커밋을 포함한다.
🎯
leopards.yaml 의 manager 를 Dooli 로 수정
커밋 메시지: Edit Leopards manager

🌏
깃 허브에서 leopards.yaml 의 coach 를 Lupi 로 수정
커밋 메시지: Edit Leopards coach

소스트리로 확인해보면 가장 상단의 커밋은 'Edit Leopards manager' 이다.
근데 깃 허브에서 작업된 커밋 순서를 확인해보면 가장 상단의 커밋은 'Edit Leopards coach' 이다.
이 상황에서 해결 방법은 아래와 같이 두가지 이다.

⭐️ no rebase (merge) 방식
$git pull --no-rebase 커밋 메세지 자동 반영
:wq
로컬 저장소에 원격 저장소가 merge

🛑
만약, $git push 를 하면 아래와 같이 작업 해줘야 한다.
$git log 를 확인하여 커밋 메세지 'Add Dongho to Leopards' 의 커밋 해시를 복사한다.
$git revert 커밋 해시
$git push --force 를 사용하여 강제로 원격 저장소도 커밋 시점을 낮추고, 맨 처음과 같은 상황 설정을 다시 하자.

⭐️ rebase 방식 (이름만 rebase 방식 (협업시 사용 OK) )
먼저 'Edit Leopards manager' 커밋 시점으로 되돌린다.
$git pull --rebase
:wq
원격 저장소에 로컬 저장소가 rebase
$git push


-- 협업 상황에서 충돌 발생 해결하기, 이런 상황은 커밋을 미포함한다.
🎯
panthers.yaml 에 가장 하단에 Maruchi 를 추가
커밋 메시지: Add Maruchi to Panthers

🌏
깃 허브에서 panthers.yaml 에 가장 하단에 Arachi 를 추가
커밋 메시지: Add Arachi to Panthers

⭐️ no rebase (merge) 방식
$git pull --no-rebase
$git add .
$git commit.

🛑
만약, $git push 를 하면 아래와 같이 작업 해줘야 한다.
$git log 를 확인하여 커밋 메세지 'Edit Leopards manager' 의 커밋 해시를 복사한다.
$git revert 커밋 해시
$git push --force 를 사용하여 강제로 원격 저장소도 커밋 시점을 낮추고, 맨 처음과 같은 상황 설정을 다시 하자.

⭐️ rebase 방식 
$git pull --rebase
$git add .
$git rebase --continue

$git push

위와 같은 상황은 충돌 시에 해결하는 과정에서 rebase 는 저장소의 종류에 따라 커밋의 수가 달라질 수 있다.
$git pull --rebase 는 원격 저장소에 로컬 저장소가 병합 된다.
에디터에서 원격 저장소에 해당하는 코드를 선택한다면 원격에 있는 커밋으로 병합이 아닌 원격 저장소 코드로만 수정이 가능하니 커밋 수가 1 로 볼 수 있다.
하지만 로컬 저장소에 해당하는 코드를 선택한다면 로컬 저장소 코드를 원격 저장소까지 푸쉬를 해야하니 커밋 수가 +1 이 증가된다.


-- 로컬 저장소의 내역 강제 푸쉬 하기
$git push --force


-- 로컬 저장소에서 브랜치를 만들어 원격 저장소에 푸쉬 해보기
$git switch -c from-local
$git push 를 하면 에러가 나오면서 $git push --set-upstream origin from-local 이라는 문구가 출력되는데,
$git push -u origin from-local 로 줄일 수 가 있다.
깃 허브에서 원격 저장소에 푸쉬한 브랜치를 확인 해본다.


-- 원격 저장소에서 수정한 내용 가져오기
🌏
깃 허브에서 panthers.yaml 에 가장 하단에 Krachi 를 추가
커밋 메시지: Add Krachi to Panthers
$git switch from-local
$git pull


-- 로컬/원격 저장소 브랜치 모두 보기
$git branch -a


-- 원격 저장소의 브랜치 로컬 저장소로 받아오기
깃 허브에서 from-remote 라는 브랜치를 만든다.	
$git branch -a 로 확인 시, 내 원격 저장소의 변경사항을 아직 안가져왔기 때문에 확인이 되질 않는다.


-- 원격 저장소의 변경사항만 가져오기
$git fetch
$git branch -a 로 확인


-- 원격 저장소의 브랜치와 같은 이름의 브랜치를 로컬 저장소에 생성하기
$git switch -t 원격 저장소 명/브랜치 명
$git switch -t origin/from-remote


-- 원격 저장소 브랜치 삭제
$git push 원격 저장소 명 --delete 원격 브랜치 명
$git push origin --delete from-remote
$git push origin --delete from-local


-- 소스트리에서 진행해보기
-- 원격 저장소 추가
먼저 'git-another-practice' 레퍼지토리를 생성한다.
소스트리로 이동하여 저장소 - 원격저장소를 클릭하여 추가한다.
원격 이름: origin2
URL/경로: https://github.com/tlswlsdntks/git-another-practice.git
Push 버튼을 클릭하여, 다음 저장소에 푸쉬 [origin2] 로 변경해준다.


-- 로컬의 내역 강제 푸쉬 하기
$git push --force


-- 로컬 저장소에서 브랜치를 만들어 원격 저장소에 푸쉬 해보기
$git switch -c from-local
$git push 를 하면 에러가 나오면서 $git push --set-upstream origin from-local 이라는 문구가 출력되는데,
$git push -u origin from-local 로 줄일 수 가 있다.
깃 허브에서 원격 저장소에 푸쉬한 브랜치를 확인 해본다.


-- 소스트리로 진행해보기
🎯
pumas.yaml 의 members 에 - Pororo 추가
커밋 메시지: Add Pororo to Pumas
소스트리로 origin/main 에 바뀐 내용 즉시 푸쉬 클릭

🌏
깃 허브의 jaguars.yaml 의 members 에 - Pinkfong 추가
커밋 메시지: Add Pinkfong to Jaguars
소스트리로 페치 및 풀

-- 로컬 저장소에서 브랜치를 만들어 원격 저장소에 푸쉬 해보기
'from-local' 이라는 이름의 브랜치를 생성하고, 푸쉬 를 클릭한다
$git push -u origin from-local 와 동일한 작업이다.

-- 원격 저장소에서 브랜치를 만들어 로컬 저장소에 풀 해보기
깃 허브에서 'from-remote' 라는 브랜치를 생성한 이후, 패치를 눌러 원격 저장소의 변경사항을 받아온다.
$git branch -a
$git branch -a 로 확인 시, 내 원격 저장소의 변경사항을 아직 안가져왔기 때문에 확인이 되질 않는다.
$git fetch

원격 저장소의 브랜치에 RMB를 누르고, 체크아웃 버튼을 클릭하여 로컬 저장소에 동일한 이름으로 저장한다.
$git switch -t origin/from-remote 와 동일한 작업이다.


-- Git 을 특별하게 만드는 것
분산 버전 관리
스냅샷 방식: 하나의 파일에 변동이 생겼을 때, 파일의 상태 "전체"를 그대로 저장해 비교


-- Git 의 3가지 공간
🎯 Working directory (에디터 기준: 빨간 글씨)
untracked: Add된 적 없는 파일, ignore 된 파일
tracked: Add된 적 있고 변경내역이 있는 파일
$git add . 명령어로 Staging area로 이동

🎯 Staging area (에디터 기준: 초록 글씨)
커밋을 위한 준비 단계
예시: 작업을 위해 선택된 파일들
$git commit 명령어로 repository로 이동

🎯 Repository
.git directory라고도 불림
커밋된 상태

💡commit 되어 레포지토리에 들어간 후 수정사항이 발생하면 tracked 파일로써 스테이징을 기다리게 된다.


-- 파일일의 삭제와 이동
tigers.yaml 를 삭제해본 뒤 $git status 로 확인하기.
파일의 삭제가 'working directory' 에 존재한다.
$git reset --hard 로 복원한다.

$git rm tigers.yaml로 삭제하고 $git status 로 확인하기.
파일의 삭제가 'Staging area' 에 존재한다.
$git reset --hard 로 복원한다.

tigers.yaml 를 zzamtigers.yaml 로 이름을 변경한 뒤 $git status 로 확인하기.
파일의 이름 변경이 'working directory' 에 존재한다.
$git add . 하고 $git status 로 확인해보면 rename 상태를 제대로 인식한다.
$git reset --hard 로 복원한다.

$git mv tigers.yaml zzamtigers.yaml 로 이름을 변경한 뒤 $git status 로 확인하기.
파일의 이름 변경이 'Staging area' 에 존재한다.
$git reset --hard 로 복원한다.


-- 파일을 staging area 에서 working directory 로 이동하기
🎯
panthers.yaml 의 members 에 - . 추가
pumas.yaml 의 members 에 - . 추가
tigers.yaml 의 members 에 - . 추가

$git add . 을 하면 모든 파일이 staging area 로 이동한다.
$git restore --staged pumas.yaml
$git status 로 확인하기.

-- staged 를 빼면 working directory 에서도 제거
$git restore pumas.yaml
과거에는 git reset HEAD (파일명) 으로 표기되었다.

$git reset --hard

💡reset의 세 가지 옵션
⭐️ soft: repository 에서 staging area 로 이동
⭐️ mixed (default): repository 에서 working directory 로 이동
⭐️ hard: 수정사항 완전히 삭제

🎯
tigers.yaml 의 members 에 - reset 추가

git commit -am 'reset mixed'
$git reset --mixed
$git status

git commit -am 'reset soft '
$git reset --soft 
$git status

git commit -am 'reset hard'
$git reset --hard
$git status


-- 깃 헤드
HEAD 라는 특정 브랜치의 최신 커밋이기도 하지만 새로운 익명 브랜치 이기도 하다.
📁 예제 다운받기
git-heads 폴더 열기

-- checkout 으로 앞뒤 한 단계 이동해보기
$git branch delta-branch
$git chekout HEAD^ 또는 $git checkout HEAD~


-- checkout 이동을 한 단계 되돌리기
$git checkout -


-- checkout 으로 앞뒤 여러 단계 이동해보기
$git checkout HEAD^^^ 또는 $git checkout HEAD~5


-- 가장 최신 커밋 시점으로 변경
$git switch 브랜치 명


-- 커밋 해시를 이용한 checkout 이동
$git checkout 커밋 해시


-- 이전으로 checkout 된 상태에서 소스트리로 HEAD 상태 보기를 보면 익명의 브랜치에 위치함을 알 수 있다.
⭐️ 기존 브랜치로 돌아오기: $git switch 브랜치 명
⭐️ 새 브랜치 만들어보기
	$git switch beta-branch
	$git checkout HEAD^
	$git swtich -c gamma-branch
	소스트리를 확인해본다.
⭐️ 새 커밋 만들어보기
	file.txt 안에 delta-branch 를 gamma-branch 로 변경한다.
	$git commit -am 'gamma 1st commit'
	소스트리를 확인해본다.


-- 브랜치의 특정 헤드로 reset 시키기
$git reset --hard HEAD^
$git reset --hard HEAD~2


-- 패치 와 풀
Fetch: 원격 저장소의 최신 커밋을 로컬 저장소로 갖고 오기만 한다. Fetch 를 하면 최신 커밋을 갖고 있는 임의의 새로운 브랜치가 파생된다고 생각하면 된다.
Pull: Fetch 를 함과 동시에 merge 또는 rebase 를 의무적으로 해야한다.


-- 원격 저장소의 메인 브랜치 해시로 이동하기
🌏
깃 허브에서 tigers.yaml 의 fetch: this 를 추가
커밋 메시지: Add fetch to Tigers

$git checkout origin/main
원격 저장소의 변경 사항을 fetch 하지 않았다.
$git fetch 
$git checkout origin/main 하면 파일이 변경된 것을 확인할 수 있다.
소스트리를 확인해보자.
현재 커밋할 변겅점이 없으니, $git pull 해도 동일하다.


-- 새로운 브랜치를 로컬 브랜치에 가져오기
🌏
깃 허브에서 new-branch 라는 이름의 브랜치를 새로 만들고,
tigers.yaml 의 new: branch 를 추가
커밋 메시지: Add new to Tigers

$git fetch
$git checkout origin/new-branch
$git switch main
$git switch -t origin/new-branch
$git branch -a


-- Git 사용 중 모르는 부분이 있을 때 도움을 받을 수 있는 기능
$git help
$git help -a


-- 해당 명령어의 설명과 옵션 보기
$git commit -h


-- 웹 사이트에서 보는 해당 명령어의 자세한 설명과 옵션
$git commit --help (-w)
웹 사이트에서 열리지 않을 시, 끝에 -w를 붙여 명시


-- 설정과 설정 값 출력
$git config (--global) user.name 'xps13'
$git config (--global) user.name


-- 현재 모든 설정 목록
$git config (--global) --list


-- 설정 변경
$git config (--global) -e


-- vim 을 에디터 (*.exe) 에서 사용
$git config --global core.editor 'code --wait'
$git config --global core.editor '경로/*.exe --wait'
wait 은 에디터에서 *.config 파일을 꺼야 다음으로 진행됨을 의미한다.


-- 운영체제 별 줄바꿈 호환 문제 해결(개행을 문자로 인식)
$git config --global core.autocrlf (윈도우 : true, 맥 : input)


-- Pull 디폴트 값 변경
merge: $git config pull.rebase false
rebase: $git config pull.rebase true


-- 기본 브랜치명 변경
$git config --global init.defaultbranch main


-- 원격 저장소에 푸쉬할 경우, 로컬 저장소와 동일한 브랜치 명으로 적용
$git config --global push.default current


--단축키를 설정
$git config --global alias.단축키 '명령어'
$git config --golbal alias.cam 'commit -am'
$git cam '메세지'


-- 컨벤션 (커밋 개발 규칙)
⭐️
타입	설명
feat	새로운 기능 추가
fix	버그 수정
docs	문서 수정
style	공백, 세미콜론 등 스타일 수정
refactor	코드 리팩토링
perf	성능 개선
test	테스트 추가
chore	빌드 과정 또는 보조 기능(문서 생성기능 등) 수정

⭐️
type: subject (커밋 내용 간략히 설명)
body (optional) (길게 설명할 필요가 있을 시, 작성)
..
..
footer (optional) (breaking point 가 있을 때, 특정 이슈에 대한 해결 작업)

예시)
feat: 압축파일 미리보기 기능 추가

사용자 편의를 위해 압축을 풀기 전에
다음과 같이 압축파일 미리보기를 할 수 있도록 함
 - 마우스 오른쪽 클릭
 - 윈도우 탐색기 또는 맥 파인더의 미리보기 창

Closes #125


-- 깃 이모지
https://gitmoji.dev/
타입을 이모지 형태로 대체할 수 있다.


-- 내용을 확인하며 hunk 별로 스테이징 하기
🎯
tigers.yaml 의 manager 를 Thanos 로 변경
tigers.yaml 의 coach 를 Ronan 로 변경
tigers.yaml 의 members 에 - Gamora, - Nebula 를 추가

🎯
leopards.yaml 의 manager 를 Peter 로 변경
leopards.yaml 의 coach 를 Rocket 로 변경
leopards.yaml 의 members 에 - Drax, - Groot 를 추가


-- hunk 별로 보기
$git add -p
(1/2) Stage this hunk [y,n,q,a,d,j,J,g,/,s,e,p,?]? 를 확인 후 입력
...
$git status


-- 변경사항을 확인하고 커밋하기
$git commit -v
$git diff 와 $git commit 을 동시에 하는 것 과 유사하다.
$git diff --staged 와 비교


-- 나머지 변경사항도 커밋하기
$git add .
$git commit
($git reset --soft HEAD^)


-- 스태시
현재 작업 디렉토리의 변경 사항을 일시적으로 저장하고, 깨끗한 작업 트리로 돌아갈 수 있게 해주는 기능입니다.

🎯
tigers.yaml 의 members 에 - Stash 를 추가

🎯
tomcats.yaml 추가
tomcats.yaml 의 내용
team: Tomcats

coach: Apache

$git add . : 스태시를 하려면 트래킹을 하고 있는 상태여야 한다.
$git stash
$git stash list
소스트리에서도 확인하자.


-- 스태시 입력하기
$git stash pop


-- 원하는 것만 스태시 해보기
🎯
leopards.yaml 의 members 에 - Stash2 를 추가
🎯
jaguars.yaml 의 members 에 - Stash3 를 추가

아래 명령어로 Stash2 만 선택하여 스태시
$git stash -p 


-- 메세지를 포함한 스테시 
아래 명령어로 Stash3 도 마저 스태시
$git stash -m 'Add Stash3'


-- 스태시 목록 보기
$git stash list


-- 스태시 선택해서 가져오기
$git stash list
$git stash apply stash@{1}


-- 스태시 선택해서 삭제하기
$git stash drop stash@{1}


-- 새 브랜치를 생성하고 스태시
$git stash branch 새 브랜치 명
새로운 브랜치에 보관용으로 사용하고, 작업이 종료되면 merge 또는 rebase 하는 용도로 사용된다.
$git add .
$git commit
소스트리에서 확인하기


-- 스태시 비우기
$git stash clear


-- 소스트리에서 사용하기
소스트리에서는 스태시 버튼을 클릭하면 커밋 되지 않은 변경점이 스태시로 간다.


-- 이전 커밋 수정하기
🎯
leopards.yaml 의 members 에 - Hoki 를 추가
커밋 메시지: Add fetch to Leopards

$git commit --amend
커밋 메세지: Add Hoki to Leopards


-- 이전 커밋에 파일 껴넣기
🎯
pumas.yaml 의 members 에 - Poki 를 추가

$git add .
$git commit --amend -m 'Add Poki to Pumas'
또는
$git commit -a --amend -m 'Add Poki to Pumas'


-- 과거의 커밋들을 수정, 삭제, 병합, 분할하기
📁 예제 다운받기
git-interactive 폴더 열기

$git rebase -i 수정시킬 대상의 직전 커밋 해시

명령어	설명
p, pick	커밋 그대로 두기
r, reword	커밋 메시지 변경
e, edit	수정을 위해 정지
d, drop	커밋 삭제
s, squash	이전 커밋에 합치기


-- 다음의 수정사항들 진행해보기
⭐️ 커밋 메세지 '횻홍' 을 '버그 수정' 으로 변경한다.
     r 명령어 사용

⭐️ 커밋 메세지 '뻘짓' 커밋 시점을 삭제한다. 
     d 명령어 사용

⭐️ 커밋 메세지 '결전의 찜질방 맵 추가중' 와 커밋 메세지 '결전의 찜질방 맵 추가 완료' 를 한 커밋으로 합친다. 
     첫 항목 뒤로 s 명령어 사용
     저장 이전에 소스트리로 확인해보면 임시 브랜치로 구분되어 있는 형태
     커밋 메시지 수정 후 저장
     저장 후, 임시 브랜치는 메인 브랜치에 rebase 된다.

⭐️ 커밋 메세지 '캐릭터 귤맨 추가, 시작메뉴 디자인 변경' 을
     커밋 메세지 '캐릭터 귤맨 추가' 와 커밋 메세지 '시작메뉴 디자인 변경 항목 나누기' 를 2개의 커밋으로 분할 한다.
     e 명령어로 수정 시작
     $git log
     $git reset (--mixed) HEAD~
     $git add file-3.txt
     $git commit -m '캐릭터 귤맨 추가'
     $git add file-4.txt
     $git commit -m '시작메뉴 디자인 변경'
     git rebase --continue


-- 관리되지 않는 파일들 삭제하기
🎯 
toClean1.txt
toClean2.txt
dir/toClean3.txt 파일을 추가

$git clean

옵션	설명
-n	삭제될 파일들 보여주기
-i	인터렉티브 모드 시작
-d	폴더 포함
-f	강제로 바로 지워버리기
-x	⚠️ .gitignore에 등록된 파일들도 삭제
💡이 옵션들은 붙여쓸 수 있다.

$git clean -nd
$git clean -id
$git clean -df
💡 흔히 쓰이는 조합: $git clean -df


-- 커밋되지 않은 변경사항 되돌리기
🎯
tigers.yaml, pumas.yaml, leopars.yaml 에  . 을 추가

$git restore .
$git restore tigers.yaml

$git add .
$git restore --staged tigers.yaml
$git status


-- 파일을 특정 해시로 복원하기
$git restore --source=커밋 해시 tiger.yaml
$git status


-- 리셋 한거 복구 하기
$git reset --hard HEAD~10
소스트리에서 확인해본다.

$git reflog
reflog 는 프로젝트가 위치한 커밋이 바뀔 때마다 기록되는 내역을 보여준다.

$git reset --hard 리셋을 한 내역의 이전 커밋 해시


-- 태그
특정 시점을 키워드로 기억하고 싶을 때 사용한다.
Semantic Versioning 정보
https://semver.org/
예시) 2.0.0 : 주.부.수
기존 버전과 호환되지 않게 API가 바뀌면 “주(主) 버전”을 올리고,
기존 버전과 호환되면서 새로운 기능을 추가할 때는 “부(部) 버전”을 올리고,
기존 버전과 호환되면서 버그를 수정한 것이라면 “수(修) 버전”을 올린다.

태그종류	설명
lightweight	특정 커밋을 가리키는 용도
annotated	작성자 정보와 날짜, 메시지, GPG 서명 포함 가능

-- lightweight 방법으로 마지막 커밋에 태그 달기
$git tag v2.0.0

-- annotated 방법으로 마지막 커밋에 태그 달기
$git tag -a v2.0.0 
$git tag v2.0.0 -m '태그 메세지'
💡-m 태그가 -a 를 암시한다.

-- 태그 확인
$git tag

--태그 내용 확인
$git show v2.0.0 

--태그 삭제
$git tag -d v2.0.0 

-- 원하는 태그 필터링해서 보기
$git tag -l 'v2.*'

-- 원하는 시점별로 태그 만들기
$git checkout HEAD~15
$git tag v1.0.0 -m '버전 1.0.0'

-- 원하는 태그 시점으로 체크아웃
$git checkout v2.0.0
💡checkout 은 익명의 브랜치로 이동하는 것과 유사하다.
$git switch main

-- 원격 저장소에 태그 푸쉬
깃 허브에서 태그를 확인해보면 아직 동기화되지 않아 확인이 안된다.
$git push 원격 저장소 명 태그 명
$git push origin v2.0.0

-- 특정 태그를 원격 저장소에서 삭제
$git push --delete 원격 저장소 명 태그 명
$git push --delete oring v2.0.0

-- 모든 태그 원격 저장소에 올리기
$git push --tags

-- 태그 별로 릴리즈 버전 만들기
https://github.com/naver/nanumfont
깃 허브 웹 사이트 우측에 릴리즈 버전을 확인할 수 있다.
💡*.zip 또는 *.tar

해당 태그 클릭 - ... - Create release
💡내용은 아래와 같이 마크다운 언어도 가능하다.
# 다운 받아 주세요
**ZIP** 압축 파일을 푼 뒤 사용하세요


-- Fast-Forward vs 3-Way-Merge
Fast-Forward: 분기한 브랜치의 커밋 히스토리가 기존 브랜치의 커밋 히스토리를 포함하고 있을 때,
                  브랜치 포인터가 Merge 과정 없이 그저 최신 커밋으로 이동하는 방식
3-Way-Merge: 각 브랜치에 새 커밋이 하나 이상 있는 경우, Merge 했을 때 두 브랜치의 코드를 합쳐서 새로운 커밋을 자동 생성해주는 방식

$git switch -c new-branch
🎯
tigers.yaml 에 merge: new-branch 를 추가

$git commit -am 'Add merge: new-branch to Tigers'
$git switch main
$git merge new-branch
또는
$git merge --no-ff new-branch
소스트리를 확인하자.


-- 체리 픽
📁 예제 다운받기
압축 푼 뒤 VS Code로 git-branch(폴더 안 폴더 주의) 폴더 열기

-- 특정 브랜치의 커밋 해시를 복사하여 다른 브랜치에 붙여넣기
$git switch main
$git cherry-pick 커밋 해시

-- 다른 브랜치에서 파생된 브랜치를 가져오기
$git rebase --onto 도착 브랜치 명 출발 브랜치 명 이동할 브랜치 명
$git rebase --onto main friut citrus
소스트리에서 확인하기
$git switch main
$git merge citrus
$git branch -d citrus

-- --rebase --onto 를 되돌리려면?
⭐️ citrus 브랜치
$git checkout '커밋 메세지 Orange 의 커밋 해시'
$git switch -c citrus
$git cherry-pick '커밋 메세지 Lemon 의 커밋 해시'
$git cherry-pick '커밋 메세지 Lime 의 커밋 해시'

⭐️ main 브랜치
$git reflog
$git reset --hard 커밋 해시


-- 다른 브랜치의 커밋들을 하나의 커밋으로 묶어 가져오기
$git switch main
$git merge --squash root
소스트리를 확인하자.
$git status
$git commit 자동 커밋 메세지
:wq
$git branch -D root


-- 깃 플로우
협업을 위한 브랜치 전략
https://nvie.com/posts/a-successful-git-branching-model/

사용되는 브랜치들
브랜치	용도
main		제품 출시/배포 (파랑)
hotfix		긴급한 버그 수정 (빨강)
release	출시/배포 전 테스트 진행(QA) (초록)
develop	다음 출시/배포를 위한 개발 진행 (노랑)
feature	기능 개발 (분홍)


-- 깃 로그 옵션들을 활용한 다양한 사용법
-- 각 커밋마다의 변경사항 함께 보기
$git log -p

-- 최근 n개 커밋만 보기
$git log -n

-- 통계와 함께 보기
$git log --stat
더 간략히: $git log --shortstat

-- 한 줄로 보기
$git log --oneline
💡$git log --pretty=oneline 과 $git log --abbrev-commit 을 줄인 것과 동일하다. 

-- 변경사항 내 단어 검색
$git log -S '단어'

-- 커밋 메시지 내 단어 검색
$git log --grep '단어'

-- 기타 제한 옵션 보기
https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%BB%A4%EB%B0%8B-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A1%B0%ED%9A%8C%ED%95%98%EA%B8%B0#limit_options

-- 자주 사용되는 그래프 로그 보기
$git log --all --decorate --oneline  --graph
💡
--all : 모든 브랜치 보기
--decorate : 브랜치, 태그 등 모든 레퍼런스 표시
--decorate=no (브랜치, 태그 정보 없앰)
--decorate=short : 기본
--decorate=full
--oneline: 한 줄로 표현
--graph : 그래프 표현

-- 포맷된 로그
$git log --graph --all --pretty=format:'%C(yellow) %h  %C(reset)%C(blue)%ad%C(reset) : %C(white)%s %C(bold green)-- %an%C(reset) %C(bold red)%d%C(reset)' --date=short
💡date 를 relative 로 바꿔보기

-- 포맷된 로그 단축키로 등록
$git config --global alias.lg "log --graph --all --pretty=format:'%C(yellow) %h  %C(reset)%C(blue)%ad%C(reset) : %C(white)%s %C(bold green)-- %an%C(reset) %C(bold red)%d%C(reset)' --date=short"
$git lg 로 사용한다.

-- 포매팅 옵션들 살펴보기
https://git-scm.com/book/ko/v2/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-%EC%BB%A4%EB%B0%8B-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A1%B0%ED%9A%8C%ED%95%98%EA%B8%B0#pretty_format


-- 변경사항 자세히 살펴보기
-- Working Directory 의 변경사항 확인
$git diff (--name-only)

-- Staged Area 의 변경사항 확인
$git diff --staged
💡staged 대신 cached 도 사용 가능하다.

-- 커밋 해시, 브랜치 간의 변경사항 확인
$git diff (--name-only) 커밋 해시 커밋 해시
$git diff (--name-only) HEAD^ HEAD~10
$git diff (--name-only) 브랜치 명 브랜치 명


-- 라인 별로 작성자 확인하기
📁 예제 다운받기
압축 푼 뒤 VS Code로 git-blame(폴더 안 폴더 주의) 폴더 열기
$git blame 파일 명

-- 라인 지정해서 작성자 확인하기
$git blame -L 시작 줄,끝 줄 파일명
$git blame -L 시작 줄,+n 파일명

⭐️ VS Code의 GitLens 확장
💡 내가 했을 땐 You 라고 표기됨


-- 이진 탐색 알고리즘
📁 예제 다운받기
압축 푼 뒤 VS Code로 git-bisect(폴더 안 폴더 주의) 폴더 열기

-- 이진 탐색 시작
$git bisect

-- 현재 커밋 시점 (v20) 에서 오류가 여부를 통지
$git bisect bad

-- v3 시점이 의심되는 상황, v3 커밋 해시로 체크아웃 
$git checkout 'v3 커밋 해시'

-- 원인을 찾을 때까지 반복
$git bisect good/bad


-- 깃 Hooks
깃 상의 이벤트마다 자동으로 실행될 스크립트를 지정한다.
프로젝트 폴더 내 .git > hooks 폴더에서 확인 가능하다.
파일 명 끝에 .sample을 없애면 파일 명에 따른 실행파일로 변경된다.
💡 pre-commit.sample:  커밋 이전에 작동하는 스크립트
     pre-push.sample: 푸쉬 이전에 작동하는 스크립트


-- gitmoji-cli로 활용예 보기
https://github.com/carloscuesta/gitmoji-cli

1. gitmoji-cli 설치
⭐️ Node.js 설치: https://nodejs.org/ko/
⭐️ 터미널에서 설치: npm i -g gitmoji-cli

2. 프로젝트의 Hooks 적용
⭐️프로젝트 내의 hooks 폴더에 추가된 'prepare-commit-msg' 파일 확인
⭐️gitmoji -i
🎯
tigers.yaml 의 members 에 - Hooks 추가

$git add .
$git commit
키보드 방향키로 이모지 선택
커밋 메세지 입력
$git push
깃 허브에서 확인

💡gitmoji-cli Hook 해제 방법
    프로젝트 내의 hooks 폴더에 추가된 'prepare-commit-msg' 파일 삭제


-- 서브 모듈
메인 프로젝트 폴더 안에 여러 프로젝트에서 사용되는 공통 모듈을 포함할 때 유용하다.

-- 서브 모듈 사용해보기
main 프로젝트 생성
$git init 로컬 저장소 생성
🎯
main 파일을 생성하고, main 추가
$git add .
$git commit -m 'first commit'
…or push an existing repository from the command line 처리

🌏
깃 허브에서 sub 레퍼지토리 생성
깃 허브에서  creating a new file - sub - sub 작성
커밋 메세지 first commit 

-- 메인 프로젝트에 서브 모듈 추가
$git submodule add 서브 모듈의 주소 (서브모듈 폴더 명)
main 프로젝트 폴더 내 서브 모듈 폴더와 .gitmodules 를 확인한다.
$git add .
$git commit -m 'add submodule'
$git push

🎯
/main 의 main 파일에 change 추가
🎯
/main/sub sub 파일에 change 추가
$git add .
$git status 를 하면 서브 모듈의 변경 사항은 Staged Area 로 이동하지 않는다.
$git commit -m 'change'
$git push

$cd sub
$git status
$git add .
$git commit -m 'another change'
$git push

main 프로젝트에서 /sub 폴더에 관한 파일의 변경사항이 있으니
$git status
$git add .
$git commit -m 'submodule commit'
$git push


-- 메인 프로젝트와 서브 모듈 가져오기
$git clone 서브 모듈의 주소

-- .gitmodules 파일에 있는 서브 모듈 정보를 .git/config에 등록한다.
$git submodule init (서브 모듈 명)

-- 서브 모듈 변동 사항 가져오기
$git submodule update
💡앞의 2가지 명령은 git submodule update --init 과 같이 한 번에 수행할 수도 있다.


-- 원격 저장소에서 서브 모듈 변동 사항 가져오기
🌏
깃 허브에서 sub 파일에 change2 를 추가
커밋 메세지 another change2

$git submodule update --remote (--recursive)
💡서브 모듈 안에 또 서브 모듈이 있을 시: --recursive 추가


-- README.md 를 활용한 문서화
GitHub의 프로젝트 페이지들 살펴보기
https://github.com/navermaps/android-map-sdk
https://github.com/sidorares/node-mysql2
https://github.com/twbs/bootstrap
💡README.md 클릭해서 'Raw' 클릭하면 해당 마크다운 형태로 확인이 가능하다.


-- README.md 만들어 보기
⭐️ 마크 다운 문법 제공 사이트
https://www.markdownguide.org/cheat-sheet/
⭐️깃 허브 제공 가이드
https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax
💡각각의 폴더 별로 README.md 파일도 제공 가능하다.


-- Pull request
변경사항을 merge 하기 전 리뷰를 거치기 위한 작업이다.
팀원들의 동의를 거친 뒤 대상 브랜치에 적용할 수 있다.

-- 풀 리퀘스트 사용해보기
새로운 브랜치 생성 후 변경사항 커밋하여 푸쉬
$git switch -c pull-request
🎯
tigers.yaml 의 members 에 - Pull-Request 추가

$git commit -am 'Add Pull-Request to Tigers'
$git push

🌏
깃 허브 레포지토리 페이지에서 Compare & pull request 버튼 클릭
또는 
~ branches에서 New pull request 클릭

메시지 작성 후 Create pull request 클릭

풀 리퀘스트 검토 후 처리하기
🌏
깃 허브 레포지토리 페이지에서 Pull requests 탭 클릭
대상 풀 리퀘스트 클릭하여 내용 검토

⭐️ 의견이 있을 시 코멘트 달기
⭐️ 반려해야 할 시 Close pull request
⭐️ 승인할 시 Merge pull request


-- Issue
버그나 문제 제보, 추가할 기능 등의 이슈 소통
⭐️ 네이버 지도 API 예제
     https://github.com/navermaps/maps.js.ncp/issues
⭐️ Flutter
     https://github.com/flutter/flutter

-- 이슈 작성해보기
🌏
깃 허브 레포지토리 페이지에서 Issues 탭 클릭
💡필요 시, label, milestone, asignee 지정
    milestone: 이슈의 주제 묶음 (특정 목표 등)

-- 이슈 확인 후 처리
코멘트 달기
관련 개발 착수 (브랜치명이나 커밋 footer에 이슈 번호 반영)

-- 컨벤션 (커밋 개발 규칙) 참고
#4 In tlswlsdntks/git-practice;· by tlswlsdntks was closed now · 버그


-- 오픈소스 프로젝트에 기여하기

-- fork
⭐️ React GitHub
     https://github.com/facebook/react
원하는 유명 프로젝트 내 레포지토리로 포크해보기

-- 코드 기여하기
코드 수정 후 pull request

-- 오픈소스 주인 관점
풀 리퀘스트 코멘트/반려/수락


-- 깃 허브로 블로그 만들기
⭐️ GitHub Pages
     https://pages.github.com/

-- 나의 GitHub Page 만들기
🌏
깃 허브에서 레포지토리 생성
❗️ 레퍼지토리 명: (내 아이디).github.io로 지어야 한다.
$git clone 레퍼지토리 주소
최상위 디렉토리에 index.html 작성
💡 VS Code 팁: ! 입력하고 엔터 누르면 기본 HTML 템플릿 생성

$git add .
$git commit
$git push
https://(내 아이디).github.io에서 사이트 확인


-- SSH 로 접속하기
SSH 프로토콜을 통한 인증, 공개키 암호화 방식 활용
username과 토큰 사용할 필요 없고, 컴퓨터 자체에 키 저장

-- SSH 키 등록하기
계정의 Settings - SSH and GPG keys

⭐️ SSH키 존재 여부 확인
     터미널(윈도우의 경우 Bash Shell)에서 ~/.ssh로 이동

⭐️ id_rsa.pub, id_ecdsa.pub, id_ed25519.pub 파일 중 하나 존재 여부 확인

⭐️ SSH 키 생성
     터미널(윈도우의 경우 Bash Shell)에서 키 생성
     $ssh-keygen -t ed25519 -C "tlswlsdntks@naver.com"
     원할 시, passphrase 입력

⭐️ 깃 허브에 키 등록
     공개키 열람하여 복사
     $ cat id_ed25519.pub
     ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIG+5dTd/agDNW5bvzvP/unvFSZldegGG0i9z5neT2nPa tlswlsdntks@naver.com

⭐️ New SSH Key 클릭하여 키 이름과 함께 등록


-- SSH로 사용해보기
$git clone 원격 저장소의 SSH 주소
