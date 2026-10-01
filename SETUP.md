# 🌱 「나를 비추는 창」 실시간 버전 설치 방법

이 버전은 **Firebase Firestore**를 사용해서 여러 휴대폰에서 같은 방에 접속하고 피드백이 실시간으로 쌓이도록 만든 웹앱입니다.

## 1. Firebase 프로젝트 만들기
1. Firebase Console에서 새 프로젝트를 만듭니다.
2. 프로젝트 안에서 **Web 앱(</>)**을 추가합니다.
3. 표시되는 `firebaseConfig` 값을 복사합니다.

## 2. 코드에 Firebase 설정 넣기
`index.html`을 메모장/VS Code 등으로 열고 아래 부분을 본인의 값으로 바꿉니다.

```js
const firebaseConfig = {
  apiKey: "...",
  authDomain: "...",
  projectId: "...",
  storageBucket: "...",
  messagingSenderId: "...",
  appId: "..."
};
```

`apiKey`는 웹 Firebase 설정에 공개되는 값이므로 그 자체를 비밀번호처럼 취급할 필요는 없습니다. 대신 Firestore 보안 규칙이 중요합니다.

## 3. Firestore 만들기
Firebase Console → Firestore Database → 데이터베이스 만들기.

그 다음 `firestore.rules`의 규칙을 Firebase Console의 Rules 탭에 넣고 게시합니다.

> 학교 발표용 프로토타입에 맞춘 공개 참여 규칙입니다. 실제 서비스로 공개할 때는 인증, 스팸 방지, 신고/삭제 기능 등을 추가하는 것이 좋습니다.

## 4. 웹에 올리기
가장 쉬운 방법은 GitHub Pages 또는 Firebase Hosting입니다.

### GitHub Pages
- GitHub 저장소를 하나 만듭니다.
- `index.html`과 `firestore.rules`를 업로드합니다.
- Settings → Pages → Deploy from branch를 선택합니다.
- 생성된 주소를 친구들에게 공유합니다.

### Firebase Hosting
Firebase CLI를 설치했다면 이 폴더에서:
```bash
firebase init hosting
firebase deploy
```

## 5. 실제 사용 흐름
1. 참가자 A가 자기 이름/별명을 입력하고 `나의 창 만들기`
2. A에게 `?respond=방ID` 링크가 생성됨
3. A가 링크를 친구들에게 공유
4. 친구들이 각자 휴대폰으로 접속
5. 특성과 피드백을 제출
6. A의 화면에서 받은 피드백이 업데이트됨
7. 내가 선택하지 않았지만 친구들이 반복해서 선택한 특성이 `🟡 맹목의 창`에 표시됨

## 6. 학교 탐구활동에서의 활용
사전 자기평가 → 친구 피드백 수집 → 자기평가와 타인평가 비교 → 맹목의 창 분석 → 자기이해의 변화와 한계 성찰 순으로 진행하면 좋습니다.

### 개인정보 주의
실명, 전화번호, 학교번호, 주소 등의 개인정보는 받지 않는 것을 권장합니다.
피드백은 외모나 민감한 개인 정보가 아니라 성격, 의사소통, 협력, 책임감 등 활동 목적에 맞는 내용으로 제한하세요.
