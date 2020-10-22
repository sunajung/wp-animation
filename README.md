# **Layout Practical Page** - by suna jung
---
<br>

## **프로젝트 설명**

> 박스모델과 레이아웃에 관한 수업을 듣고 만든 실습 페이지입니다.<br>
> 4주차 실습 내용 뿐 아니라, 3주차 CSS 수업때 배운 내용도 활용하여 홈페이지 화면을 제작했습니다.<br> 
> '음악과 공연'에 관한 커뮤니티를 주제로 잡아 제작했으며, 레이아웃 구성은 다음과 같습니다. <br>
> - `header` : navigator 포함
> - `section 1` : 광고 배너
> - `section 2` : 계열사 (그리드 활용), 네이버 시작화면에서 '언론사' 가 모여있는 느낌으로 제작했습니다.
> - `section 3` : 상영중인 공연 광고
> - `section 4` : 개발자 설명란
> - `aside` : 인기토픽과 찜한공연란, 네이버와 쿠팡 사이트를 참고했습니다.
> - `footer` : 저작권 표시

<br>

## **주요 코드 설명** 
---
<br>

> 구조적인 관점에서 주요 코드를 설명해드리겠습니다.<br>
> 크게 **`header, section 1~4, aside, footer** 로 구성됩니다. <br>

### **[ Header ]**

<br>

- `flex` 속성을 이용하여 네비게이터를 포함한 헤더를 제작했습니다.
- header의 경우 `position`을 `fixed`로 하여 스크롤을 해도 고정되도록 했습니다. 또한 `z-index`에 큰 값을 주어 스크롤을 내렸을 때 본문의 내용이 헤더의 밑에 가려져서 안보이도록 구현했습니다.
- `min-width` 속성을 주어, 부모요소 기준으로 지정 값 이하가 되면 더이상 줄어들지 않도록 제작했습니다.

``` html
<style>
    header {
            min-width: 1120px;
            width: 100%;<!--부모 요소 기준으로 width 지정해주어야 반응형이 가능함.-->
            height: 80px;
            position: fixed;<!--스크롤을 내려도 헤더가 고정되도록-->
            z-index: 99999; <!--헤더가 본문보다 위에 위치하도록-->
            margin: 0 0 5px 0; <!--헤더 아래쪽에만 마진을 줌-->
            min-height: 10px;
    }
</style>
```

- nav의 경우 `position`을 `absolute`로 하여 유연하게 위치할 수 있도록했고, 네비게이터 요소에 각각 left, right 값을 주어 반응형 홈페이지처럼<br>
  크기에 맞게 변화하도록 했습니다.


``` html
<style>
    .nav,
    .left,
    .right {
            position: absolute;
            top: 0;
            display: flex;
            height: 80px;
            align-items: center;
            background-color: white;
    }

    .left {
            left: 200px;
            align-items: flex-end;
        }

    .right {
            width: 500px;
            right: 0px;
            align-items: flex-end;
        }

</style>      
```


<br><br>

### **[ SECTION 1 ]**

<br>

- 배경 이미지로 광고를 넣고, 그 위에 `grid`를 활용해서 광고 선택창을 만들었습니다. 강의에서 보여주신 사이트를 참고했습니다.
- style의 .backcontainer에 사용한 그리드를 구현했습니다. 4행 1열로 이루어져있으며, `position`을 `absolute`로 하여 원하는 위치에 위치시켰습니다.<br>

``` html
<style>
.backcontainer {
            display: grid;
            position: absolute;
            margin: 15px 10px 10px 80%;
            grid-template: repeat(4, 90px) / repeat(1, 180px);
        }
</style>
```

- section1의 자식 선택자를 이용하여 테두리를 주었습니다.

``` html
<style>
.section1>div>div {
            border: 3px solid rgb(112, 110, 110);
            box-shadow:3px 3px 3px 3px #999;
            width: 100%;
            height: 100%;
        }
</style>
```

<br> 

**+) 3개의 광고선택창에 마우스를 갖다대면 사진이 변합니다.**

<br><br>

### **[ SECTION 2 & 3 ]**

<br>

- section 2와 3을 한 라인에 배열하고 싶어서, `display: inline-block` 을 활용했습니다.
- 계열사를 나타내는 12개의 그리드와, 상영중인 공연 광고가 한줄에 배열됩니다.
- section2와 3을 묶어, `top-wrapper` 클래스를 주었습니다.

``` html
<style>
        .section2 {
            display: inline-block;
            position: static;
            /* top: 330px; */
        }

        .section3 {
            float:right;
            display: inline-block;
            /* top:320px; */
            left: 0px;
            margin-right: 10px;
            margin-left: 60px;

        }

        .top-wrapper{
         display: inline-block;
       }
</style>
```
<br><br>

### **[ SECTION 4 ]**

<br>

- profile 클래스를 이용하여 사진을 왼쪽에 `float`으로 위치시켰고, 사진 옆에 글씨를 배열했습니다.

``` html
<style>
        .profile{
            width: 250px;
            height: 250px; 
            border-radius: 30%;
            overflow: hidden;
            margin: 10px 20px 10px 0;
            float:left;
        }
</style>
```
<br><br>

### **[ aside ]**

<br>

- `float:right`를 활용해 홈페이지 가장 오른쪽에 위치시켰고, 크기 조정을 통해 `section 2~4` 세로 길이에 맞게 위치되도록 했습니다.
- 자식선택자를 이용하여 하위 사진들의 속성등을 지정해주었습니다.

``` html
<style>
        aside{
         position:absolute;
         padding-bottom: 50px;
         padding-left:14px;
         border : 1px solid black;
         display:inline;
         width:330px;
         right:30px;
         float:right;
      }
      .like-show>div:not(.item){
         width:100px;
         display:inline-block;
      }
      .like-show>div>img{
         display:block;
      }
      .like-show>div>p{
         width:100px;
         display:inline-block;
         margin: 0 0 0 0;
      }
</style>
```
<br><br>

### **[ footer ]**

<br>

- 마진과 패딩을 이용하여 위치만 잡아주었습니다.

<br><br>

## **비고 및 고찰** 
---
<br>
레이아웃 과제였지만, 지난 시간에 배운 css 내용도 같이 적용시켜 웹 페이지를 구성했습니다. 만들다 보니 재밌어서, 외적인 부분도 신경을 썼습니다. <br>
만들고 나니 별거 없어보이는 웹페이지만, 총 개발시간만 12시간이 걸렸습니다. 8시간의 강의를 듣고나니 어떤걸 어디에 적용해야겠다, 같은 것은 눈에 보였지만 바로 적용할 수 있는 수준은 아니어서 수업자료와 구글을 벗삼아 제작했습니다. <br><br>


### **사전조사** <br>

레이아웃 수업인만큼 현행 사이트들은 어떠한 레이아웃을 적용하고 있는지 사전조사가 필요하다고 생각하여 <br>
- `오늘의 집`
- `마켓컬리`
- `쿠팡`
- `티몬`
- `네이버`
- `디자인 외주 사이트`   를 참고했습니다.<br>

 가장 인기있는 사이트들과, 디자인에 신경써야하는 디자인 외주 사이트라면 트렌드를 잘 파악할 수 있을거라 생각했기 때문입니다.<br><br>
교수님께서 교재엔없지만 수업에서 알려주신, **네비게이션이 위에 있는 구조**  가 가장 많이 쓰였고,<br> 가운데에 광고를 많이 넣는 것 같아 aside에 네비게이터를 넣으려는 계획을 수정했습니다. <br><br>

### **실제 제작** <br>

교수님께서 수업시간에 알려주신 코드를 활용하여, 헤더를 제작했는데 여기서도 문제가 꽤 많았습니다.<br>

**1. 헤더를 스크롤 해도 고정하려고함.** <br>
=> 단순히 position:fixed 했으나 헤더와 내용이 겹쳐서 떴습니다. 그래서 padding 을 주었으나 스크롤 시 그대로 겹치는 문제가 여전히 존재했습니다. <br>
강의 시간에 배운 z-index가 생각났고, 이를 99999로 줘서 해결했습니다.

**2. 메뉴있는 부분제외 글씨가 또 겹쳐보임** <br>
=> 헤더 태그 css에 너비 100% 높이 80px을 지정했습니다. 너비 100%로 부모요소 크기만큼 그대로 받아와야 헤더 부분이 완벽히 가려질 수 있었습니다.

**3. 화면이 줄어들때, 최소크기 지정.** <br>
=> header는 fixed로 아예 고정하고, .nav .left.right의 position은 absolute로 바꿨습니다. 부모의 좌표계 기준으로 위치정하기가 가능해서 header는 0.0에 고정해두고 min-width를 일정 수치로 두면 header가 일정 크기 이하로 줄어들지 않았습니다.<br><br>
=>  .right는 부모의 맨 오른쪽 위치하게 했습니다. 따라서 .right의 부모가 header기 때문에 header 창 크기를 줄이면 계속 따라서 줄어드는 문제가 있었습니다. 이는 min-width를 설정하여 고정함으로써 해결했습니다.

---

<br>
 이와 같이 사소한 문제들이 제작할 때 너무많았습니다. 하나만 바꿔도 디자인이 붕 떠버렸고 부모와 자식관계도 생각할 때 어려움이 많았습니다. <br><br>
 강의에서 배운 내용을 최대한 많이 적용하려고 grid, flex, position fixed와 absolute, padding, margin 개념등을 많이 사용했고, 그 외에 css로 꾸미기도 적용해봤습니다. <br><br>
 비례를 맞추는것이 시간 투자한것만큼 결과가 눈으로 잘 보이지 않아 중간에 후회도 많이했지만 제작하고나니 실력이 많이 는 것 같아 기쁩니다. 다음에 진짜 홈페이지를 제작할 때는 수월하게 제작할 수 있을 것 같습니다! 피드백 해주셨으면 좋겠습니다!! <br>
<br><br>

## **기타 사항** 
---
<br>
레이아웃 요소외에도, 디테일에 신경쓴 부분들 입니다.<br><br>

> - 스크롤 해도 헤더 고정됨.
> - nav 메뉴바에 마우스 갖다대면 글씨 색 변함. (장바구니와 돋보기도 색이 변해요!)
> - 광고 배너부분 그리드칸에 마우스를 갖다대면 광고가 변합니다.
> - 화면 크기를 조정하면 홈페이지 요소들도 크기가 변합니다. 가장 적정한 사이즈로 모두 맞춰놨습니다.
> - 찜한 공연에 있는 사진 외에는, 전부 제작한 사진 입니다!