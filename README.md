#  模写 HTML/CSS/JavaScript(jQuery)課題

CodeStepで模写をしました。とても親切な模写サイトとして有名かと思います。

今回は下記のデモサイトをもとに、jQueryのコード解説をいたします。

# ©️

【HTML/CSS コーディング練習】[上級編：ギャラリーサイト／スクロールイベント](https://code-step.com/gallery-menu/)

模写サイト: [デモサイト](https://code-step.com/demo/html/gallery/)(© Codestep)

著作権フリーのコードを利用しました（[詳細](https://code-step.com/coding-copyright/)）。サイトでの公開が可能です。

<br>

# コード

<details><summary><b>index.html</b></summary><div>

```html
<!DOCTYPE html>
<html lang="ja">
  <head>
    <meta charset="utf-8">
    <title>FA EXHIBITION</title>
    <meta name="description" content="お花の展示サイト（模写）">

    <!-- レスポンシブデザイン用の設定 -->
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="icon" href="img/favicon.ico">

    <!-- リセットCSSとフォントの読み込み -->
    <link rel="stylesheet" href="https://unpkg.com/ress/dist/ress.min.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300;400&display=swap" rel="stylesheet">

    <!-- スタイルシートとスクリプトの読み込み -->
    <link rel="stylesheet" href="css/style.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
    <script src="js/jquery.inview.min.js"></script>
    <script src="js/main.js"></script>
  </head>

  <body>
    <!-- ヘッダー -->
    <header id="header">
      <div class="logo">
        <a href="#"><img src="img/logo.svg" alt="FA EXHIBITION"></a>
      </div>

      <!-- ナビゲーションメニュー -->
      <nav id="navi">
        <ul class="menu">
          <li><a href="#">TOP</a></li>
          <li><a href="#information">INFORMATION</a></li>
          <li><a href="#gallery">GALLERY</a></li>
          <li><a href="#access">ACCESS</a></li>
          <li><a href="#contact">CONTACT</a></li>
        </ul>
      </nav>

      <!-- ハンバーガーメニュー -->
      <div class="hamburger">
        <span></span>
        <span></span>
        <span></span>
      </div>
    </header>

    <!-- コンテンツコンテナ -->
    <div class="container">
      <main>

        <!-- メインビジュアル -->
        <div id="mainvisual">
          <img src="img/mainvisual1.jpg" alt="">
          <img src="img/mainvisual2.jpg" alt="">
          <img src="img/mainvisual3.jpg" alt="">
        </div>

        <!-- サイトタイトル -->
        <h1 class="site-title inview fadein">Hello Flower!<br>FA EXHIBITION 2023</h1>

        <!-- Information -->
        <section id="information" class="inview fadein">
          <h2 class="section-title">INFORMATION</h2>
          <p>
            <span class="info-date-en">2023 JUL 1(SAT)-3(MON)</span>
            <span class="info-time-en">DAY1 10am-6pm OTHER 10am-5:30pm</span>
          </p>
          <p class="info-place">at PARK SIDE HALL</p>
          <p class="info-date-ja">
            2023年7月1日(土) ー 3日(月)<br>
            Day1 10時〜18時  その他 10時〜17時30分
          </p>
        </section>

        <!-- サイドボタン -->
        <div id="side-btn">
          <a href="#">FOR VISITOR</a>
          <a href="#">FOR EXHIBITOR</a>
        </div>

        <!-- Gallery -->
        <section id="gallery" class="wrapper">
          <h2 class="section-title inview fadein">GALLERY</h2>
          <ul class="list">
            <!-- 画像リスト -->
            <li class="inview fadein"><img src="img/flower1.jpg" alt=""></li>
            <li class="inview fadein"><img src="img/flower2.jpg" alt=""></li>
            <li class="inview fadein"><img src="img/flower3.jpg" alt=""></li>
            <li class="inview fadein"><img src="img/flower4.jpg" alt=""></li>
            <li class="inview fadein"><img src="img/flower5.jpg" alt=""></li>
            <li class="inview fadein"><img src="img/flower6.jpg" alt=""></li>
          </ul>
        </section>

        <!-- Access -->
        <section id="access">
          <h2 class="section-title">ACCESS</h2>
          <p class="place">PARK SIDE HALL</p>
          <p class="address">
            〒152-0035 東京都目黒区自由が丘xxxxxx PARK SIDE HALL<br>
            PARK SIDE HALL, xxxxxx Jiyugaoka, Meguro-ku, Tokyo
          </p>
          <p class="contact">
            Tel: 03-1111-1111<br>
            E-mail: info@xxxxxxx.jp
          </p>
          <a class="btn" href="#" target="_blank">GOOGLE MAP</a>
        </section>

        <!-- Contact -->
        <section id="contact" class="wrapper">
          <h2 class="section-title">CONTACT</h2>
          <a class="btn" href="#">出展に関するお問い合わせ</a>
          <a class="btn" href="#">その他のお問い合わせ</a>
        </section>

        <!-- Accessの背景画像 -->
        <div class="bg"></div>
      </main>

      <!-- フッター -->
      <footer id="footer">
        <div>
          <p>FA EXHIBITION</p>
          <p>〒152-0035 東京都目黒区自由が丘xxxxxx PARK SIDE HALL</p>
          <p class="contact">
            Tel: 03-1111-xxxx<br>
            E-mail: info@xxxxxxx.jp
          </p>
          <ul class="sns">
            <li><a href="#" target="_blank">Twitter</a></li>
            <li><a href="#" target="_blank">Facebook</a></li>
            <li><a href="#" target="_blank">Instagram</a></li>
          </ul>
        </div>
        <ul class="copyright">
          <li><a href="#">PRIVACY POLICY</a></li>
          <li>&copy; FA EXHIBITION</li>
        </ul>
      </footer>
    </div>
  </body>
</html>
```

</div></details>

<br>

<details><summary><b>style.css</b></summary><div>

```css
@charset "UTF-8";

html {
  font-size: 100%;
}

body {
  color: #050507;
  font-family: 'Source Sans Pro', sans-serif;
  font-weight: 300;
}

/* リンクの色と下線をなくす */
a {
  color: #fff;
  text-decoration: none;
}

/* 画像の最大幅を100%に設定 */
img {
  max-width: 100%;
  vertical-align: bottom;
}

/* リストのマーカーをなくす */
li {
  list-style: none;
}

/* h1タグ用のスタイル */
.site-title {
  font-size: 6.25rem;
  font-weight: 300;
  letter-spacing: 0.03em;
  margin: 100px 0;
}

/* h2タグ用のスタイル */
.section-title {
  border-bottom: solid 1px #fff;
  /* 下線をテキストと同じ幅にあわせるために設定 */
  display: inline-block;
  font-size: 3.75rem;
  font-weight: 300;
  letter-spacing: 0.03em;
  margin-bottom: 45px;
}

/* コンテンツ幅を設定するための共通クラス */
.wrapper {
  max-width: 800px;
  padding: 0 30px;
  margin: 0 auto;
}

/* MainとFooter全体を囲むクラス */
.container {
  background: #050507;
  color: #fff;
  text-align: center;
}

/*
サイドボタン
初期状態は「translateY(60px);」で画面の右側に隠しておく
Galleryのタイトルが画面下にきたタイミングで、jQueryでCSSを変更してボタンをスライドしながら表示する
Accessのタイトルが画面下にきたタイミングで、jQueryでCSSを変更してボタンをスライドしながら非表示にする
*/
#side-btn {
  border: solid 1px #fff;
  position: fixed;
  right: -144px;
  bottom: 200px;
  transform: rotate(-90deg) translateY(60px);
  transition: 0.6s;
  z-index: 30;
}

/* サイドボタン内のリンク */
#side-btn a {
  width: 165px;
  font-size: 0.875rem;
  display: inline-block;
  letter-spacing: 0.1em;
  padding: 15px 0;
  transition: 0.3s;
}

/* サイドボタン内の最後のリンクに左側のボーダーを追加 */
#side-btn a:last-of-type {
  border-left: solid 1px #fff;
}

/* サイドボタン内のリンクのホバー時の透明度を変更 */
#side-btn a:hover {
  opacity: 0.7;
}

/*
Accessの背景画像
初期状態は「display: none;」で非表示にしておく
Accessのタイトルが画面下にきたタイミングで、jQueryのfadeInで表示する
Contactのタイトルが画面下にきたタイミングで、jQueryのfadeOutで非表示にする
「position: fixed;」で固定し「width: 100vw;」「height: 100vh;」で全画面表示する
*/
.bg {
  background: url("../img/bg.jpg") center center repeat !important;
  width: 100vw;
  height: 100vh;
  position: fixed;
  top: 0;
  left: 0;
  display: none;
  z-index: 10;
}

/*
フェード表示
InformationとGalleryの画像を下からふわっと表示させるためのクラス
「transform: translate(0, 50%);」で下にさげた状態で、
「opacity: 0;」で非表示にしておく
*/
.fadein {
  opacity: 0;
  transform: translate(0, 50%);
  transition: 2s;
}

/*
fadeinクラスの要素が画面下にきたタイミングで、jQueryのinviewにてshowクラスを追加して「transform: translate(0, 0);」と「opacity: 1;」で表示させる
*/
.fadein.show {
  transform: translate(0, 0);
  opacity: 1;
}

/*-------------------------------------------
ヘッダー
-------------------------------------------*/
/*
ヘッダーロゴ
初期状態は「display: none;」で非表示にしておく
所定のスクロール位置にきたらjQueryのfadeInで表示する
*/
.logo {
  line-height: 1px;
  position: fixed;
  top: 35px;
  left: 30px;
  /* 一番上にくるように設定 */
  z-index: 40;
  display: none;
}

.logo a {
  display: block;
}

/*
ハンバーガ―メニュー
初期状態は「display: none;」で非表示にしておく
所定のスクロール位置にきたらjQueryのfadeInで表示する
*/
.hamburger {
  width: 42px;
  height: 42px;
  cursor: pointer;
  position: fixed;
  top: 20px;
  right: 25px;
  /* 一番上にくるように設定 */
  z-index: 40;
  display: none;
}

.hamburger span {
  width: 30px;
  height: 1px;
  background-color: #fff;
  position: absolute;
  left: 6px;
  transition: 0.5s ease-in-out;
}

.hamburger span:nth-child(1) {
  top: 11px;
}

.hamburger span:nth-child(2) {
  top: 21px;
}

.hamburger span:nth-child(3) {
  top: 31px;
}

.hamburger.active span:nth-child(1) {
  top: 21px;
  left: 6px;
  transform: rotate(-45deg);
}

.hamburger.active span:nth-child(2),
.hamburger.active span:nth-child(3) {
  top: 21px;
  transform: rotate(45deg);
}

#navi {
  width: 100%;
  background-color: #fff;
  color: #050507;
  position: fixed;
  top: 0;
  left: 0;
  text-align: center;
  transform: translateY(-100%);
  transition: 0.6s;
  /* ロゴ、ハンバーガーより下でAccessページの背景画像よりも上にくるよう設定 */
  z-index: 30;
}

#navi ul {
  width: 100%;
  background-color: #050507;
  padding: 80px 0 30px 0;
}

#navi ul li {
  padding: 10px 0;
}

#navi ul li a {
  display: block;
}

/*
メニュー表示
ハンバーガーメニューがクリックされた際に、jQueryで#naviにactiveクラスを追加して、
メニューを上から下にスライドさせて表示する
*/
#navi.active {
  transform: translateY(0%);
}

/*-------------------------------------------
メインビジュアル
-------------------------------------------*/
#mainvisual {
  display: flex;
  justify-content: center;
  /* スクロールで画像を拡大させた際に、横スクロールが出ないよう設定 */
  overflow-x: hidden;
}

/*
スクロールしたタイミングでjQueryにて画像を拡大するが、
その際に画像が縮まないよう「flex-shrink: 0;」を設定する
*/
#mainvisual img {
  width: calc(100%/3);
  height: 100vh;
  flex-shrink: 0;
  object-fit: cover;
}

/*-------------------------------------------
Information
-------------------------------------------*/
#information {
  margin-bottom: 140px;
}

#information .info-date-en {
  display: block;
  font-size: 1.5rem;
}

#information .info-time-en {
  display: block;
  font-size: 1.125rem;
}

#information .info-place {
  font-size: 2.5rem;
  font-weight: 400;
  margin: 20px 0;
}

#information .info-date-ja {
  font-size: 1.125rem;
}

/*-------------------------------------------
Gallery
-------------------------------------------*/
#gallery {
  margin-bottom: 480px;
}

#gallery .list li {
  margin-bottom: 60px;
}

#gallery .list li img {
  width: 48%;
}

/* 奇数のliタグは左寄せ */
#gallery .list li:nth-child(odd) {
  text-align: left;
}

/* 偶数のliタグは右寄せ */
#gallery .list li:nth-child(even) {
  text-align: right;
}

/*-------------------------------------------
Access
-------------------------------------------*/
/*
「z-index: 20;」でコンテンツが背景画像の上にくるようにする
※デフォルトのposition（static）では、z-indexを指定できないため。
「position: relative;」設定する
*/
#access {
  margin-bottom: 480px;
  position: relative;
  z-index: 20;
}

#access .place {
  font-size: 1.75rem;
  font-weight: 400;
  margin-bottom: 20px;
}

#access .address {
  margin-bottom: 20px;
}

#access .contact {
  margin-bottom: 30px;
}

#access .btn {
  border: solid 1px #fff;
  color: #fff;
  display: inline-block;
  padding: 15px 82px;
  transition: 0.3s;
}

#access .btn:hover {
  background-color: #050507;
}

/*-------------------------------------------
Contact
-------------------------------------------*/
/*
「z-index: 20;」でコンテンツが背景画像の上にくるようにする
*/
#contact {
  margin-bottom: 200px;
  position: relative;
  z-index: 20;
}

#contact .btn {
  width: 400px;
  border: solid 1px #7d7d7d;
  color: #fff;
  display: block;
  padding: 30px 0;
  margin: 0 auto 20px auto;
  position: relative;
  transition: 0.3s;
}

/*
ボタン矢印
*/
#contact .btn::before,
#contact .btn::after {
  content: "";
  position: absolute;
  right: -40px;
  height: 1px;
  background-color: #fff;
  transition: 0.3s;
}

/*
矢印の直線部分
*/
#contact .btn::before {
  width: 120px;
  top: 48px;
}

/*
矢印の先端部分
「rotate(25deg)」で角度をつける
*/
#contact .btn::after {
  width: 15px;
  top: 45px;
  transform: rotate(25deg);
}

#contact .btn:hover {
  opacity: 0.7;
}

#contact .btn:hover::before,
#contact .btn:hover::after {
  right: -50px;
}

/*-------------------------------------------
Footer
-------------------------------------------*/
#footer {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  border-top: solid 1px #fff;
  font-size: 0.75rem;
  padding: 80px 30px;
  text-align: left;
}

#footer p {
  line-height: 1.6;
}

#footer .sns {
  display: flex;
  align-items: center;
  margin-top: 30px;
}

#footer .sns li {
  margin-right: 15px;
}

#footer .copyright {
  display: flex;
  align-items: center;
}

#footer .copyright li:last-child {
  margin-left: 30px;
}

/*-------------------------------------------
SP
-------------------------------------------*/
@media screen and (max-width: 900px) {
  .site-title {
    font-size: 3rem;
    margin: 50px 0;
  }

  .section-title {
    font-size: 2rem;
  }

  /*-------------------------------------------
  Information
  -------------------------------------------*/
  #information {
    margin-bottom: 80px;
  }

  #information .info-date-en,
  #information .info-time-en,
  #information .info-date-ja {
    font-size: 1rem;
  }

  #information .info-place {
    font-size: 2rem;
  }

  /*-------------------------------------------
  Gallery
  -------------------------------------------*/
  #gallery {
    margin-bottom: 280px;
  }

  #gallery .list li {
    margin-bottom: 30px;
  }

  #gallery .list li img {
    width: 100%;
  }

  /*-------------------------------------------
  Access
  -------------------------------------------*/
  #access {
    margin-bottom: 280px;
  }

  /*-------------------------------------------
  Contact
  -------------------------------------------*/
  #contact .btn {
    width: 100%;
  }

  /*
  スマホの時は矢印を消す
  */
  #contact .btn::before,
  #contact .btn::after {
    content: none;
  }

  /*-------------------------------------------
  Footer
  -------------------------------------------*/
  #footer {
    flex-direction: column;
    align-items: flex-start;
    padding: 60px 30px;
  }

  #footer .sns {
    margin-bottom: 30px;
  }
}
```
</div></details>

<br>

<details><summary><b>main.js</b></summary><div>

```js
$(function () {

  /*=================================================
  ハンバーガ―メニュー
  ===================================================*/
  // ハンバーガーメニューをクリックした時
  $('.hamburger').on('click', function () {
    // ハンバーガーメニューの共通処理を呼び出す
    hamburger();
  });
  // メニューのリンクをクリックした時
  $('#navi a').on('click', function () {
    // ハンバーガーメニューの共通処理を呼び出す
    hamburger();
  });

  /*=================================================
  スムーススクロール
  ===================================================*/
  // ページ内リンクのイベント
  $('a[href^="#"]').click(function () {
    // リンクを取得
    let href = $(this).attr("href");
    // ジャンプ先のid名をセット
    let target = $(href == "#" || href == "" ? 'html' : href);
    // トップからジャンプ先の要素までの距離を取得
    let position = target.offset().top;
    // animateでスムーススクロールを行う
    // 600はスクロール速度で単位はミリ秒
    $("html, body").animate({ scrollTop: position }, 600, "swing");
    return false;
  });

  /*=================================================
  フェード表示
  ===================================================*/
  $(".inview").on("inview", function (event, isInView) {
    if (isInView) {
      // 要素（inviewクラス）が表示されたらshowクラスを追加する
      $(this).stop().addClass("show");
    }
  });

  /*=================================================
  スクロール時のイベント
  ===================================================*/
  $(window).scroll(function () {
    // スクロール位置を取得
    let scroll = $(window).scrollTop();

    /*=================================================
    メインビジュアルの拡大・縮小
    ===================================================*/
    mv_scale(scroll);

    /*=================================================
    ロゴ、ハンバーガーメニューの表示
    ===================================================*/
    // スクロール位置が520pxを超えた場合
    if (scroll > 520) {
      // ロゴとハンバーガ―メニュをfadeInで表示する
      $('.logo').fadeIn(500);
      $('.hamburger').fadeIn(500);
      // スクロール位置が520px未満の場合
    } else {
      // ロゴとハンバーガ―メニュをfadeOutで非表示にする
      $('.logo').fadeOut(500);
      $('.hamburger').fadeOut(500);
    }

    /*=================================================
    サイドボタンを表示
    ===================================================*/
    // 画面下から#galleryまでの距離を取得
    let gallery_position = $('#gallery').offset().top - $(window).height();
    // 画面下から#accessまでの距離を取得
    let access_position = $('#access').offset().top - $(window).height();

    // window.innerWidthで画面幅を取得
    // PC表示の場合の処理（画面幅が900pxより大きい場合　※900pxはCSSのブレークポイントとあわせる）
    if (window.innerWidth > 900) {
      // #galleryが表示された場合（スクロール位置が、画面下から#galleryまでの距離を超えた場合）
      if (scroll > gallery_position) {
        // #accessが表示されるまでの間は、#side-btnを横からスライドさせて表示する
        if (scroll < access_position) {
          $('#side-btn').css({
            'transform': 'rotate(-90deg) translateY(0)'
          });
          // #accessが表示されたら、#side-btnをスライドさせて非表示にする
        } else {
          $('#side-btn').css({
            'transform': 'rotate(-90deg) translateY(60px)'
          });
        }
        // #galleryが表示される前は、#side-btnをスライドさせて非表示にする
      } else {
        $('#side-btn').css({
          'transform': 'rotate(-90deg) translateY(60px)'
        });
      }
    }

    /*=================================================
    Accessの背景画像を表示
    ===================================================*/
    // 画面下から#contactまでの距離を取得
    let contact_position = $('#contact').offset().top - $(window).height();

    // #accessが表示された場合
    if (scroll > access_position) {
      // #contactが表示されるまでの間は、背景画像をfadeInで表示する
      if (scroll < contact_position) {
        $('.bg').fadeIn(500);
      } else {
        $('.bg').fadeOut(500);
      }
      // #accessが表示される前の場合
    } else {
      // 背景画像を表示しない
      $('.bg').fadeOut(500);
    }
  });

  /*=================================================
  画面読み込み時と画面幅変更時のイベント
  ===================================================*/
  $(window).on('load resize', function () {
    // スクロール位置を取得
    let scroll = $(window).scrollTop();

    /*=================================================
    メインビジュアルの拡大・縮小
    ===================================================*/
    mv_scale(scroll);
  });
});

/*=================================================
ハンバーガ―メニュー（共通処理）
===================================================*/
// ハンバーガーメニューをクリックした時とメニュー内のリンクをクリックした時の
// 処理が同じなので処理を共通化する
function hamburger() {
  // toggleClassを使用することで、hamburgerクラスにactiveクラスが存在する場合は削除、
  // 存在しない場合を追加する処理を自動で行ってくれる
  $('.hamburger').toggleClass('active');

  if ($('.hamburger').hasClass('active')) {
    // hamburgerクラスにactiveクラスが存在する場合は、naviにもactiveクラスを追加する
    $('#navi').addClass('active');
  } else {
    // hamburgerクラスにactiveクラスが存在しない場合は、naviからactiveクラスを削除する
    $('#navi').removeClass('active');
  }
}

/*=================================================
メインビジュアルの拡大・縮小（共通処理）
===================================================*/
function mv_scale(scroll) {
  // window.innerWidthで画面幅を取得
  // PC表示の場合の処理（画面幅が900pxより大きい場合　※900pxはCSSのブレークポイントとあわせる）
  if (window.innerWidth > 900) {
    // メインビジュアルのCSS（width）を変更する
    // widthの値をスクロール量にあわせて増やすことで画像を拡大させる
    $('#mainvisual img').css({
      'width': 100 / 3 + scroll / 10 + '%'
    });
    // スマホ表示の場合の処理（画面幅が900px以下の場合）
  } else {
    // メインビジュアルのCSS（width）を変更する
    // widthの値をスクロール量にあわせて減らすことで画像を縮小させる
    $('#mainvisual img').css({
      'width': 100 - scroll / 10 + '%'
    });
  }
}
```

<br>

</div></details>


# jQueryの仕様

## 使用箇所
1. ハンバーガーメニュー
2. スムーススクロール
3. フェード表示
4. スクロール時のイベント
5. 画面読み込み時と画面幅変更時のイベント
6. ハンバーガーメニューとメインビジュアルの拡大・縮小の共通処理


<br>

## ハンバーガーメニュー
520pxのスクロール位置に達すると、ハンバーガーメニューが表示されます。メニューをクリックすると、メニューがスライドして全画面で表示されます。クリックイベントの処理には、jQueryの`.on()`メソッドを使用します。

```js
$('.hamburger').on('click', function() { ... });
```

上記のコードは、"hamburger"クラスの要素がクリックされたときに実行される関数を定義しています。同様に、メニュー内のリンクのクリックイベントも処理します。

## スムーススクロール
ページ内のアンカーリンク（`<a>`要素の`href`属性が"#"で始まるもの）のクリックイベントを処理するために、jQueryの`.click()`メソッドを使用します。

```js
$('a[href^="#"]').click(function() { ... });
```

上記のコードは、条件にマッチするリンクがクリックされたときに実行される関数を定義しています。実際のスクロール処理は、`$("html, body").animate({scrollTop: position}, 600, "swing");`のように、`.animate()`メソッドを使用して行われます。

## フェード表示
特定の要素（".inview"クラスが付いた要素）が画面内に表示されると、表示された要素に".show"クラスが追加されます。`.on()`メソッドを使用して、要素が画面内に表示されるたびに発火する"inview"イベントに対して処理を行います。

## スクロール時のイベント
```js
$(window).scroll(function() { ... });
```

上記のコードは、ウィンドウのスクロールイベントの処理です。スクロールイベントが発火するたびに、定義された関数を実行します。具体的な処理としては、スクロール位置に応じて要素の表示や非表示を切り替える処理や背景画像の表示を制御する処理があります。

## 画面読み込み時と画面幅変更時のイベント
```js
$(window).on('load resize', function() { ... });
```

ページの読み込みが完了した時やウィンドウのサイズが変更された時に、定義された関数を実行します。

## ハンバーガーメニューとメインビジュアルの拡大・縮小の共通処理
ハンバーガーメニューの共通処理は、`hamburger()`関数で定義されています。この関数では、ハンバーガーメニューの状態に応じて要素にクラスを追加または削除します。

メインビジュアルの拡大・縮小の共通処理は、`mv_scale()`関数で定義されています。この関数では、スクロール位置に応じてメインビジュアルの幅を変更します。

<details><summary><b>その他の仕様</b></summary><div>

フォント:
- 使用するフォント: Source Sans Pro (Google Fonts)

メインビジュアル:
- PC: スクロールダウンすると画像が拡大します。
- スマホ: 画像を縮小します。

サイドボタン (PCのみ):
- GALLERYタイトルが画面下に表示されると、右から左にスライドして右下に表示されます。
- ACCESSタイトルが画面下に表示されると、スライドして非表示になります。

CONTACTのボタン:
- ホバー時には、透明度がかかり矢印が右に動きます。
- スマホの場合、矢印は表示されません。

レスポンシブ:
- ブレークポイント: 900px

</div></details>
