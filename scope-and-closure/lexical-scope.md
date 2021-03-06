# 렉시컬 스코프
> 중첩 스코프(Nested Scope) 내에서 변수를 찾을 때 사용하는 '규칙의 집합'<br>
> 프로그래머가 코드를 작성할 때 함수를 어디에 선언하는지에 따라 정의되는 스코프<br>
- 스코프
  - 렉시컬 스코프(Lexical Scope)
  - 동적 스코프(Dynamic Scope)
  
<br>

### 렉스타임 (렉싱타임 Lexing Time)
> 토크나이징 & 렉싱: 소스 코드 문자열을 분석<br>
> 변수와 스코프 블록을 어디서 작성하는가에 기초해서 렉서 (Lexer)가 코드를 처리할 때 확정<br>

- 스코프 버블
```javascript
function foo(a) {
	var b = a * 2;
	
	function bar(c) {
		console.log(a, b, c);
	}
	
	bar(b * 3);
}

foo(2); // 2, 4, 12
```
> 교차할 수 있는 벤다이어그램이 아니다.<br>
> 섀도잉 (Shadowing): 여러 중첩 스코프 층에 걸쳐 같은 확인자 이름을 정의할 수 있다, (안쪽 확인자가 바깥쪽의 확인자를 가리키는 것)<br>

<br>

### 렉시컬 속이기
> 컴파일 단계에서 수행한 스코프 검색과 관련된 최적화 작업을 무산시킨다...
- `eval`: 런타임에 수정
  - 렉시컬 스코프를 런타임에 수정할 수 있다.
  - `setTimeout()`, `setInterval()`: 이 방법은 구식에다가 없어질 예정이니 사용하지 말자!
  - `new Function()`: `eval()` 보다는 안전하지만, 여전히 코드에 사용하지 않는 것이 좋다.
- `with`
  - 블록 내부에서 렉시컬 참조를 수행한다.
  - 속성이 있는 경우, 가져와서 사용하지만
  - 속성이 없는 경우, 글로벌 변수가 생성된다.
  
  
