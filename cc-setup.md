# CC 셋업 가이드

> Claude Code를 설치하고 사용하기 위한 환경 세팅 가이드입니다.

---

## 0단계: GitHub 계정 만들기

이미 계정이 있다면 건너뛰세요.

1. https://github.com 접속
2. `Sign up` 클릭
3. 이메일, 비밀번호, 사용자명 입력
4. 봇 방지 퍼즐을 풀어야 합니다 — 동물 방향 맞추기, 별자리 찾기 등 다소 황당한 퍼즐이 여러 번 나옵니다. 인내심을 갖고 풀어주세요 😇
5. 이메일로 온 인증 코드 입력하면 가입 완료

> 사용자명은 나중에 바꿀 수 있으니 너무 고민하지 않아도 됩니다.

---

## 1단계: 패키지 매니저 설치

앱 설치를 터미널 한 줄로 해결해주는 도구입니다. 웹사이트 찾아가서 다운로드 버튼 누르고... 할 필요 없어요.

### macOS — Homebrew

**1) 터미널을 엽니다**

Spotlight 검색(⌘ + Space)에서 `터미널` 또는 `Terminal`을 검색해서 열어주세요.

**2) 아래 명령어를 복사해서 붙여넣고 Enter를 누릅니다**

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> 이 명령어가 하는 일: Homebrew 공식 설치 스크립트를 인터넷에서 받아와서 실행합니다.

**3) 비밀번호를 입력합니다**

맥 로그인 비밀번호를 물어봅니다. 입력할 때 화면에 아무것도 안 나오는 게 정상이에요. 그냥 입력하고 Enter 치면 됩니다.

**4) 설치 완료 확인**

설치가 끝나면 아래 명령어로 확인:

```bash
brew --version
```

`Homebrew 4.x.x` 같은 버전이 나오면 성공입니다.

**⚠️ Apple Silicon Mac (M1/M2/M3/M4) 추가 설정**

설치 끝나고 터미널에 이런 메시지가 나올 수 있습니다:

```
==> Next steps:
- Run these commands in your terminal to add Homebrew to your PATH...
```

이 경우, 안내에 나온 두 줄을 그대로 복사해서 실행하세요:

```bash
echo >> ~/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
```

그 다음 터미널을 껐다가 다시 열면 됩니다.

### Windows — winget (이미 설치되어 있음!)

Windows 10/11에는 **winget**이 이미 내장되어 있습니다. 별도 설치가 필요 없어요.

**PowerShell을 엽니다**

시작 메뉴에서 `PowerShell`을 검색해서 열어주세요.

> ⚠️ `명령 프롬프트(cmd)`가 아닌 **PowerShell**에서 실행해주세요. 파란색 아이콘이 PowerShell입니다.

확인:

```powershell
winget --version
```

버전이 나오면 바로 2단계로 넘어가세요.

---

## 2단계: 필요한 앱 설치

### macOS

터미널에서:

```bash
brew install --cask claude-code github visual-studio-code warp
```

### Windows

PowerShell에서:

```powershell
winget install -e --id Git.Git
winget install -e --id Anthropic.ClaudeCode
winget install -e --id GitHub.GitHubDesktop
winget install -e --id Microsoft.VisualStudioCode
winget install -e --id Warp.Warp
```

> Windows는 **Git for Windows**가 추가로 필요합니다. 맨 위에 `Git.Git`이 그 역할입니다.
> 각각 Git, Claude Code, GitHub Desktop, VS Code, Warp를 설치합니다.
> Warp는 모던 터미널 앱입니다. 기본 터미널 대신 사용하면 편합니다.

---

## 3단계: 프로젝트 클론

우리 콘텐츠 레포를 로컬에 받아야 합니다.

**GitHub Desktop 앱**을 열고:

1. `File` → `Clone Repository` (또는 첫 화면에서 `Clone a Repository`)
2. URL 탭 선택
3. 아래 주소 입력:

```
플젝 하나 셋업 필요함
```

4. 저장 위치를 확인하고 `Clone` 클릭


---

## 4단계: VS Code로 프로젝트 열기

1. **VS Code** 앱을 실행합니다
2. `File` → `Open Folder` (또는 시작 화면에서 `Open Folder`)
3. 방금 클론한 `프로젝트` 폴더를 선택합니다

> 폴더를 VS Code 아이콘이나 창 위에 드래그해서 놓아도 됩니다.

### Auto Save 켜기

파일을 수정할 때마다 일일이 저장하지 않아도 되도록 자동 저장을 켜두세요.

- macOS: `File` → `Auto Save` 클릭 (체크 표시가 나오면 활성화된 상태)
- Windows: `File` → `Auto Save` 클릭 (동일)

---

## 5단계: 확장 프로그램 설치

프로젝트를 열면 오른쪽 하단에 **"이 작업 영역에 권장되는 확장이 있습니다"** 알림이 뜹니다.

`설치` (또는 `Install All`)를 눌러주세요.

> 레포에 `.vscode` 설정이 포함되어 있어서, 작업에 필요한 확장 프로그램을 자동으로 추천해줍니다.
> 알림을 놓쳤다면: 왼쪽 사이드바 확장 탭(블록 아이콘) → 검색창에 `@recommended` 입력하면 목록이 나옵니다.

---

## 6단계: Claude Code 실행

확장 프로그램이 설치되었으면, VS Code 안에서 바로 Claude Code를 쓸 수 있습니다.

- macOS: `⌘ + Shift + P` → `Claude Code: Open` 검색 후 Enter
- Windows: `Ctrl + Shift + P` → `Claude Code: Open` 검색 후 Enter

> 또는 상단 바에 Claude 아이콘이 생겼다면 클릭해도 됩니다.

이제 AI 에이전트와 함께 작업할 준비가 됐습니다.

---

## 💡 팁: Antigravity도 있어요

구글이 만든 **Antigravity**라는 코드 에디터도 있습니다. VS Code를 기반으로 만들어져서 UI와 사용법이 거의 동일하고, Gemini AI가 내장되어 있어요.

궁금하면 설치해서 써보세요:

- macOS: `brew install --cask antigravity`
- Windows: `winget install -e --id Google.Antigravity`

VS Code 확장 프로그램도 대부분 호환되고, Claude Code 확장도 동일하게 동작합니다.
