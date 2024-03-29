## this

- 자신이 **속한 객체** 또는 자신이 **생성할 인스턴스**를 가리키는 `자기 참조 변수`다.
- this 를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.
- this가 가리키는 값, 즉 this 바인딩은 `함수 호출 방식`에 의해 동적으로 결정된다.

> 💡 **this 바인딩**
> 바인딩이란 식별자와 값을 연결하는 과정을 의미한다.  
> this 바인딩은 `this` _(키워드로 분류되지만 식별자 역할을 한다)_ 와 this가 `가리킬 객체`를 바인딩하는 것이다.

## this 바인딩 종류

- 전역에서의 `this` : `window`
- 일반 함수 내부에서의 `this` : `window`
- 메서드 내부에서의 `this` : `메서드를 호출한 객체`
- 생성자 함수 내부에서의 `this` : 생성자 함수가 생성할 `인스턴스`

this는 객체의 프로퍼티나 메서드를 참조하기 위한 자기 참조 변수이므로 일반적으로 객체의 메서드 내부 또는 생성자 함수 내부에서만 의미가 있다. 따라서 **strict mode**에서는 일반 함수 내부의 this에는 `undefined`가 바인딩된다. _**일반 함수 내부에서는 사용할 필요가 없기 때문이다.**_

## 함수 호출 방식에 따른 this 바인딩

- 일반 함수 호출  
  ㄴ 전역 객체가 바인딩된다 **_어떠한 함수(중첩,콜백 포함)라도 일반 함수로 호출되면 전역 객체가 바인딩된다._**
- 메서드 호출  
  ㄴ 메서드를 호출한 객체를 가리킨다
- 생성자 함수 호출  
  ㄴ 생성자 함수가 생성한 인스턴스를 가리킨다
- apply, call, bind 메서드에 의한 간접 호출  
  ㄴ 첫 번째 인수로 전달한 객체

> 💡 메서드 내에서 정의한 중첩 함수 또는 메서드에게 전달한 콜백함수가 일반 함수로 호출될 때 전역 객체를 바인딩하는 것은 문제가 있다  
> 이들 함수는 외부 함수를 돕는 헬퍼 함수의 역할을 하므로 외부 함수의 일부 로직을 대신하는 경우가 대부분이다. 하지만 외부 함수인 메서드와 이들의 this 가 일치하지 않는다는 것은 헬퍼 함수로서 동작하기 어렵게 만든다.

### +apply, call, bind

- apply, call 메서드의 본질적인 기능은 `함수를 호출`하는 것이다. 함수를 호출하면 첫 번째 인수로 전달한 특정 객체를 호출한 함수의 this 에 바인딩한다.
- bind 메서드는 함수를 호출하지 않고 다만 첫 번째 인수로 전달한 값으로 `this 바인딩이 교체된 함수`를 새롭게 생성해 반환한다. → **함수를 호출하지는 않으므로 명시적으로 호출해야 한다.**
