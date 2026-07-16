# B tv 전단지 번호 변경기

전화번호를 입력하면 SK 브로드밴드 B tv 전단지 이미지의 "가입 및 혜택 문의" 번호가
자동으로 교체된 PNG 이미지를 만들어주는 웹페이지입니다. 별도 프로그램 설치나 서버 없이
정적 파일(HTML)만으로 동작합니다.

## 폴더 구성

```
b-tv-flyer-generator/
├── index.html          # 실행 파일 (이 파일을 열면 바로 사용 가능)
└── assets/
    └── flyer-base.png  # 원본 전단지 이미지 (번호가 없는 상태로 지워짐)
```

## GitHub Pages로 올리는 방법

1. GitHub에서 새 저장소(Repository)를 만듭니다. (예: `b-tv-flyer-generator`)
2. 이 폴더 안의 `index.html`과 `assets` 폴더를 통째로 저장소에 업로드합니다.
   - GitHub 웹사이트에서 "Add file → Upload files"로 드래그해서 올려도 됩니다.
   - 또는 터미널에서:
     ```
     git init
     git add .
     git commit -m "b tv 전단지 번호 변경기"
     git branch -M main
     git remote add origin https://github.com/내계정/b-tv-flyer-generator.git
     git push -u origin main
     ```
3. 저장소의 **Settings → Pages**로 이동합니다.
4. **Branch**를 `main`, 폴더를 `/ (root)`로 선택하고 저장합니다.
5. 1~2분 후 `https://내계정.github.io/b-tv-flyer-generator/` 주소로 접속하면
   누구나 전화번호를 입력해서 자기 번호가 들어간 이미지를 바로 만들고 다운로드할 수 있습니다.

## 사용법 (접속 후)

1. 전화번호 입력창에 번호를 입력합니다. (숫자만 입력해도 자동으로 하이픈이 붙습니다)
2. 아래 미리보기 이미지가 실시간으로 바뀝니다.
3. "이미지 다운로드" 버튼을 누르면 완성된 PNG 파일이 저장됩니다.

## 다른 이미지로 바꾸고 싶다면

`assets/flyer-base.png`를 다른 전단지 이미지로 교체하고,
`index.html` 안의 아래 값들을 새 이미지에 맞게 수정하면 됩니다.

```js
const NATIVE_W = 705, NATIVE_H = 1010;      // 이미지 실제 가로/세로 픽셀
const ERASE_BOX = { x: 434, y: 946, w: 256, h: 46 }; // 기존 번호를 가릴 영역
const BG_COLOR = "rgb(237,243,253)";        // 그 영역의 배경색
const TEXT_START_X = 444;                   // 새 번호 텍스트 시작 x좌표
const TEXT_BASELINE_Y = 982;                // 새 번호 텍스트 기준선 y좌표
const TEXT_MAX_RIGHT = 682;                 // 텍스트가 넘어가면 안 되는 오른쪽 한계
```
