# this 용법

1. inline 이벤트 속성에 기술된 this는 태그객체 자신을 의미함. 
    ```html
    <input type="checkbox" name="subject" id="subject1" onchange="subjectChanged(this);">
    ```
2. 일반함수 안에서 사용된 this는 전역객체 window를 가리킴
   ```javascript
   function test12(){
        console.log(this); // window
        console.log(this === window); // true
    }
    ```
3. 화살표함수의 this는 부모환경의 this를 가져다 쓴다. 전역에 선언된 화살표함수는 전역의 this를 가져다 쓴다.
    ```javascript
    const test13 = () => {
        console.log(this); // window
        console.log(this === window); // true
    };
    ```
4. 객체의 일반함수 안에서 this는 현재객체를 가리킨다.
    ```javascript
    const obj = {
        id: 'honggd',
        getId: function(){
            // 부모의 this는 현재 객체
            (() => {
                console.log('getId안의 화살표 함수 : ', this);
            })();
            return this.id;
        }
    }
    console.log(obj.getId());
    ```
5. 생성자함수에서 this는 현재객체를 가리킨다. (new 연산자 호출 필수)
    ```js
    function Pet(name, breed, weight, age, color){
        this.name = name;
        this.breed = breed;
        this.weight = weight;
        this.age = age;
        this.color = color;
        // 단축문법 불가
        this.bark = function(){
            return this.weight < 10 ? '왈왈' : '멍멍';
        };
    }
    ```