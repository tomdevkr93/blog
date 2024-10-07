---
title: Hoisting(호이스팅) 알아보기
published: 2024-10-07
description: '실행 컨텍스트에 이어서 호이스팅이 무엇인지 알아보자'
image: ''
tags: ['front-end', 'Hoisting', 'javaScript', '호이스팅']
category: 'front-end'
draft: false 
---

## 호이스팅 (Hoisting)

호이스팅은 JavaScript에서 변수와 함수 선언이 그들이 포함된 스코프의 최상단으로 "끌어올려지는" 것처럼 동작하는 현상입니다. 이는 실행 컨텍스트의 생성 단계와 직접적으로 연관되어 있습니다.

### 실행 컨텍스트 생성과 호이스팅의 관계

1. **실행 컨텍스트 생성 단계** 
   - JavaScript 엔진이 코드를 실행하기 전에, 실행 컨텍스트를 생성합니다.
   - 이 단계에서 변수와 함수 선언을 스캔하고 메모리에 저장합니다.

2. **var 변수의 호이스팅**
   - `var`로 선언된 변수들은 선언부만 스코프의 최상단으로 끌어올려집니다.
   - 이때 변수들은 `undefined`로 초기화됩니다.

3. **함수 선언의 호이스팅**
   - 함수 선언은 전체가 끌어올려지며, 함수 전체가 메모리에 저장됩니다.

### 호이스팅 예시

```javascript
console.log(x); // undefined
var x = 5;

foo(); // "Hello, I'm hoisted!"
function foo() {
    console.log("Hello, I'm hoisted!");
}

console.log(y); // ReferenceError: y is not defined
let y = 10;
```

이 코드가 실행될 때
1. 실행 컨텍스트가 생성됩니다.
2. `x` 변수 선언이 호이스팅되어 `undefined`로 초기화됩니다.
3. `foo` 함수 전체가 호이스팅됩니다.
4. 코드가 한 줄씩 실행됩니다.
5. `y`는 `let`으로 선언되어 호이스팅되지만, 초기화되지 않은 상태로 "일시적 사각지대(Temporal Dead Zone)"에 놓이게 됩니다.

### 호이스팅과 실행 컨텍스트의 관계

- 호이스팅은 실행 컨텍스트의 생성 단계에서 발생합니다.
- 변수와 함수 선언은 해당 실행 컨텍스트의 변수 객체(Variable Object)에 추가됩니다.
- 이로 인해 코드의 실행 전에 변수와 함수가 메모리에 할당되어 있게 됩니다.

### 주의사항

- `let`과 `const`로 선언된 변수도 호이스팅되지만, 초기화되지 않은 상태로 남아 "일시적 사각지대"에 놓이게 됩니다.
- 함수 표현식은 변수 선언만 호이스팅되며, 함수 할당은 호이스팅되지 않습니다.

```javascript
console.log(functionExpression); // undefined
var functionExpression = function() {
    console.log("I'm not hoisted");
};
```

호이스팅을 이해하는 것은 JavaScript의 실행 컨텍스트와 스코프 작동 방식을 깊이 이해하는 데 중요합니다. 이를 통해 예기치 않은 동작을 방지하고 더 효과적인 코드를 작성할 수 있습니다.
