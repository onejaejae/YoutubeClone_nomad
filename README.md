# WETUBE 학습 내용 정리



### node js를 사용할 때 장점

-   많은 데이터를 다룰 때

-   minimalistic

-    0부터 시작해서 모든것을 customize 가능

### Express

-   프레임워크 - 우리가 원하는 것을 더 빨리 만들 수 있도록 해준다

-   node js에서 작동하는 프레임워크 express  => 서버 개발을 용이하게 해준다.

 ✨장점 : 안정적

### NPM(Node Package Manager)

-    중앙집중화 시스템(자바스크립트와 관련된 모든 패키지를 다운, 업데이트, 삭제, 공유 할 수 있다)

-    node.js를 다운 받으면 npm도 함께 다운로드 된다.

-    npm init

### get, post 방식

-   get 방식

    1.  쿼리스트링의 길이 제한으로 대용량 데이터 처리 불가

    2.  쿼리스트링에 데이터가 노출됨(보안성 취약, 그렇다고 post 방식이 보안이 뛰어나지는 않다)


  
-   post 방식

    1. 정보 전달을 할 경우( ex. 로그인, 댓글)

    2. 대용량 데이터 처리 용이

### 🤷‍♀️ Babel 이란?

 최신의 js코드를 작성하면 이전 버전으로 변경해줌

IE를 포함한 모든 브라우저가 이러한 최신 ES6 문법을 다 지원하지 못하기에 효율성과 유지보수등의 이유로 코드자체는 ES6으로 구현해야 하지만 실행환경이 뒷받쳐주지 못함으로 인해 버전 차이가 발생하게 된다.

Babel은 이러한 문제점을 해결해주는 녀석으로 ES6,7로 작성된 코드를 브라우저가 인식할 수 있는 ES5로 변환시켜주는 Transpiler 이다. 

대단한 친구임에 분명함에도 주의해야 할 점은 Babel을 사용한다고 해서 ES6,ES7 함수를 다 사용할수 있는 건 아니다.
따라서 프로그램이 처음 시작될 때 브라우저에서 지원하지 않은 함수를 검사해 처리해 주는 작업이 이루어져야 한다.( babel-ployfill )

출처 

https://mwoo526.tistory.com/32

https://www.daleseo.com/js-babel-node/


#### 📌 babel node 


ES6(ES2105) 이상의 최신 자바스크립트 문법으로 작성된 코드가 노드JS(NodeJS)에서 실행이 안 되는 경우가 종종있습니다. 이럴 경우 어쩔 수 없이 예전 자바스크립트 문법으로 코드를 재작성하기도 하는데요. 이번 포스트에서는 자바스크립트 Transpiler인 Babel을 이용하여 이 문제를 해결

🔊 ES 6 모듈 사용법(bable을 사용할 경우 사용)

export default app; → import app from "./app";

export const 변수명; → import { 변수명 } from "./파일명";

### devDependencies 란?

프로젝트를 실행하는데 필요한 라이브러리가 아닌 개발자에게 필요한 라이브러리를 설치할 경우
npm install 패키지명 -D 로 다운하면 package.json에 devDependencies변수에 담긴다.

### middleware 란?

-   실행순서 : 위에서 부터 아래로 실행된다

-   express에서의 모든 함수는 middleware가 될 수 있다.

-   주의 : next()가 꼭 필요하다 !! 안그럼 다음에 실행할 콜백함수가 실행하지 못한다!!

-   각개적용 = 라우팅 - 콜백 사이에 직접 위치해줌.

-   모두적용 = app.use () 로 적용해주고, 해당 코드 아래에 있는 모든 코드에 적용됨.

📌 주요 미들웨어

1. Morgan - 어플리케이션에서 발생하는 모든일을 로깅하는 미들웨어 (로그(로깅) : 무슨 일이 어디서 일어났는지 기록)

2. helmet - 기초 보안 담당

3. cookieParser - cookie를 전달받아서 사용할 수 있도록 만들어주는 미들웨어, 사용자 인증 같은 곳에서 쿠키를 검사할 때 사용

4. bodyParser - 사용자가 웹사이트로 전달하는 정보들을 검사하는 미들웨어, request 정보에서 form이나 json 형태로 된 body를 검사

    이 패키지가 내부적으로 본문을 해석해 req.body에 추가해준다.

    예를 들어 JSON 형식으로 { name: 'backback' , book: 'nodejs' }를 본문으로 보낸다면, req.body에 그대로 들어간다.

    URL-encoded 형식으로 name=backback&book=node.js를 본문으로 보낸다면, req.body에 { name : 'backback' , book: 'nodejs' }가 들어간다.

    body-parser가 모든 본문을 해석해주는 것은 아니다.

    multipart/form-data 같은 폼을 통해 전송된 데이터는 해석하지 못한다.

    출처: https://backback.tistory.com/336 [Back Ground]

   app.use(bodyParser.json()) : HTTP Body부분에서 JSON 형식의 데이터 전달 방식을 파싱해주겠다는 소리. 즉, aplication/json 방식의 Content-Type 데이터를 받아준다.

   bodyParser.urlencoded({...}) : aplication/   x-www-form-urlencoded 방식의 Content-Type    데이터를 받아준다. 일반적으로 <form> 태그를    활용하여 post 전송 시, Ajax로 서버에 데이터를    요청하는 경우 등이 이에 해당한다. 형태는    "key=value&key2=value2"로 전송된다.
   
   { extended : false } : 내부적으로 querystring    library를 사용. True로 하면 내부적으로 qs    library를 사용하여 URL-encoded data를 파싱.
   
   extended 는 중첩된 객체표현을 허용할지 말지를    정하는 옵션입니다. 객체 안에 객체를 파싱할 수    있게하려면 true로 하라고 하네요


### MVC 패턴이란(just pattern❗)


M : Model(database) - 여기서는 mongoDB

V : View(template) - 여기서는 pug를 사용해 구현

C : Control(function) - function 부분을 따로 폴더에 담아 분리해서 관리한다

📢 One single source of truth(한 곳에서만 정보를 저장) =>  더 나은 코드를 만들어주는 원칙

우리 코드에서는 라우팅 하는 URL 주소를 routes.js 라는 파일을 만들어 따로 보관하므로써 재사용성을 확보함.


### pug 설치 & 셋팅 & 적용

1. 퍼그 설치 - ( npm install pug)

2. 퍼그 템플릿 적용법 1 (Express Set)

    -   app.set("view engine", "pug"); 라고 해주면,
기본적으로 (default) = views 폴더에서 pug 파일을 찾음.

3. 퍼그 적용하기 (render)

    -    컨트롤러에서, res.render 로 pug파일이름을 주면, 얘가 퍼그파일을 불러옴.

[Layout]

1. 레이아웃 짜기 (main) 이라는 하나의 레이아웃을 짜고,

2. 각 페이지별로 바뀔부분만을 적용할 수 있도록(컴포넌트로활용)해 contents 부분만을 바꾼다.

3. 바꿀 부분을 block content << 라고 잡아줬다. (content 부분은 바뀔 수 있음 그냥 block의 이름임)

4. 다른 페이지에서 extends layout/main << 이렇게 임포트해오고,

5. block content (main에 있던것과 똑같이) 적어준 뒤, 해당 부분에 적용할 콘텐츠를 적는다.

#### 📌 partial


컴포넌트화 시켜서 분리할 수 있음. (header & footer)

include를 사용함.


*pug에서도 자바스크립트를 사용할 수 있음 

 다음과  같은 방식 → #{ js Code }

*div는 쓰지않아도 div가 적용됨.




### 자바스크립트 ES6 모듈 내보내기/불러오기 

-   ES6에서는 export, import로 모듈을 손쉽게 제작, 가져다 쓸수 있습니다.

- 항상 알파벳순으로 import 하는 것이 좋은 습관이다.


✨ ES6 모듈 시스템의 이점

아무래도 ES6 모듈 시스템이 좀 더 최신 스팩이다 보니 CommonJS 방식 대비 여러가지 이점들이 있습니다. 
우선 import, from, export, default처럼 모듈 관리 전용 키워드를 사용하기 때문에 가독성이 좋습니다. 
또한 비동기 방식으로 작동하고 모듈에서 실제로 쓰이는 부분만 불러오기 때문에 성능과 메모리 부분에서 유리한 측면이 있습니다. 
뿐만 아니라 앞으로 다룰 Named Parameter와 같이 CommonJS에서는 지원하지 않는 기능들이 있습니다.

출처 https://www.daleseo.com/js-module-import/

### 📌 dotenv는 언제 쓰는가?

node.js 로 개발을 하면서, 포트, DB 관련 정보 등 전역으로 필요한 여러 정보들이 존재한다. node.js 에서는 dotenv 패키지를 통해 환경변수 파일을 외부에 만들고, 관리할 수 있다.  특히, 깃허브 등에 오픈소스로 프로젝트를 공개할때, DB 계정 정보를 소스코드 내에 하드코딩하지 않고, 외부 환경변수 파일에 작성하고, .gitignore 을 통해 제외하면 안전하다.

출처 https://hudi.kr/node-js-dotenv-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0/

관련자료 https://brunch.co.kr/@topherlee/73


### ✔ express 정적 파일 서비스

    static-file-folder에 대한 설정 없이 서버에 저장된 파일의 경로를 클라이언트에서 사용한다면?
만약 파일이 이미지라면, 해당 url을 서버로 요청하지만, 서버에서 파일경로를 찾지못해 404 not found 응답과, 이미지-엑박을 출력한다.

출처 https://velog.io/@hwang-eunji/nodejs-6-express-static%ED%8C%8C%EC%9D%BC-%ED%8F%B4%EB%8D%94-%EC%84%A4%EC%A0%95


### ESLint && Prettier 함께 사용하기

ESLint는 JavaScript, JSX의 정적 분석 도구로 오픈 소스 프로젝트입니다. 코드를 분석해 문법적인 오류나 안티 패턴을 찾아주고 일관된 코드 스타일로 작성하도록 도와줍니다. JSLint, JSHint와 같이 다른 JavaScript 정적 분석 도구들도 있지만, ESLint가 커스터마이징이 쉽고 확장성이 뛰어나 많이 쓰이고 있는 추세입니다. ESLint는 스타일 가이드를 좀 더 편리하게 적용하기 위해 사용하기도 하는데, 외부에 공개되어 많은 개발자가 사용 중인 Airbnb Style Guide, Google Style Guide 가 그 대표적인 예입니다.

ESLint는 코팅 스타일 가이드를 따르지 않거나 문제가 있는 코드나 안티 패턴을 찾기 위해 사용하는 Javascript linter이다. ESLint는 처음부터 유용하게 사용할 수 있는 스타일 가이드(built-in rule)을 제공하지만 개발자가 자신의 스타일 가이드를 작성할 수도 있다.

✔ 가급적이 아니라 필히 사용할 것을 권장한다.

 

📌설치법 

https://nomadcoders.co/wetube/lectures/46 

📌 관련 링크

https://pravusid.kr/javascript/2019/03/10/eslint-prettier.html

https://tech.kakao.com/2019/12/05/make-better-use-of-eslint/

https://poiemaweb.com/eslint


### Path.resolve() vs Path.join()

📣 resolve만의 차이점

오른쪽에서 왼쪽으로 경로들을 읽습니다.

'/폴더명' 을 만나면 절대경로로 인식해서 그 경로를 바로 반환합니다.

따라서 경로를 합치기위해서는 상대경로인 './폴더명' 으로 확실하게 구분해줘야합니다.

쉽게 말하자면 path.resolve는 오른쪽에서 왼쪽으로 읽으며 path.join 과는 다르게 상대경로와 절대경로를 인식하여 구분합니다!

📌 오른쪽 부터 읽어서 절대 경로가 확인된 것부터 다시 오른쪽으로 합친다❕

📌 만약 / 를 끝까지 만나지 못하면 /현재경로/생성된경로 형태로 결과를 리턴한다.
 
출처: https://programming119.tistory.com/106 [개발자 아저씨들 힘을모아]


###  Webpack이란 ? 

Webpack은 의존 관계에 있는 모듈들을 하나의 자바스크립트 파일로 번들링하는 모듈 번들러이다. Webpack을 사용하면 의존 모듈이 하나의 파일로 번들링되므로 별도의 모듈 로더가 필요없다. 그리고 다수의 자바스크립트 파일을 하나의 파일로 번들링하므로 html 파일에서 script 태그로 다수의 자바스크립트 파일을 로드해야 하는 번거로움도 사라진다.

출처 

https://poiemaweb.com/es6-babel-webpack-2

자료 

https://www.zerocho.com/category/Webpack/post/58aa916d745ca90018e5301d

### passport-local, passport-local-mongoose 회원가입, 로그인하기

-   Passport는 NodeJS 의 사용자 인증 미들웨어이다. 
  
    -   Express 기반으로 local 인증( 사용자 ID, PW ) , GitHub, FaceeBook, Google, Twitter를 이용한 사용자 인증을 지원한다
   
    -   Express 와 Express-Session 미들웨어를 연동함으로 더 유연한 기능을 제공함


-   passport-local-mongoose는 passport를 사용한 사용자 이름 및 비밀번호 로그인을 단순화하는 Mongoose 플러그인 이다.

출처 

https://studyingych.tistory.com/45

관련자료

 https://darrengwon.tistory.com/189

 https://gaemi606.tistory.com/34

 
https://www.zerocho.com/category/NodeJS/post/57b7101ecfbef617003bf457


### passport-github 사용하기😁

관련 링크

http://www.passportjs.org/packages/passport-github/

https://darrengwon.tistory.com/212?category=877507

### Web Content Security


관련 링크

https://w01fgang.tistory.com/147

https://velog.io/@taylorkwon92/%EC%98%A4%EB%8A%98%EC%9D%98-TIL

### passport facebook 사용하기

### localtunnel

-   우리의 로컬 서버를 https 터널로 만들어 준다

✔ 링크 

http://localtunnel.github.io/www/

### nodemailer 예제

https://miryang.dev/2019/04/25/nodejs-page-3/


http://www.passportjs.org/docs/
(localStrategy 변경해서 로그인 부분 구현 해보자)

### Muter Upload to AWS S3

1) AWS S3 버킷 생성 후 엑세스 퍼블릭으로 만들기

2) IM에서 사용자 추가 후(AmazonS3FullAccess)  KEY, SECRET KEY env 파일에 저장(📌 key, secret key는 한번 밖에 확인 못하므로 바로 저장해놓기)

3) npm i aws-sdk multer-s3


### 배포 에러

'babel-node'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는
배치 파일이 아닙니다.

=> $ npm i -D @babel/node




