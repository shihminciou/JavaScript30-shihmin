### 01 - JavaScript Drum Kit
[Challenge 1](https://shihminciou.github.io/JavaScript30-shihmin/01%20-%20JavaScript%20Drum%20Kit/)

原作是「模擬一個打鼓頁面，透過敲打鍵盤ASDFGHJK時，該相對應字母除了會變大變亮外，對應的鼓聲也會隨之響起。」

根據以上需求，快速思考流程如下
1. 得到每個鍵盤字母的"值"
2. 將每個key code綁定在鍵盤事件中
3. 點擊下去時會觸發音效以及毫秒般變大變亮的毫秒效果 

實作如下：

```javascript
const keys = Array.from(document.querySelectorAll('.key'));
```

* querySelectorAll會回傳non-live NodeList，這是什麼...待查，也會有跟getElementById或name或class的議題。
* 靜態方法Array.from會回傳類陣列(array-like)物件???，比較特別的是他還能拆字串陣列，像下方例子，待查
```javascript
Array.from('foo')
// ["f","o","o"]
```

接下來把取得的所有keys都加上 <b> transitionend </b> 這個"css過渡完成時發生的事件"

主要是為了停止播放playing這件事情

```javascript
keys.forEach(key => key.addEventListener('transitionend',removeTransition));
```

* forEach，把陣列裡每個元素傳入給指定的函式
* 箭頭函數，=>，每次看都要重新想一下，
// 只有一個參數時,括號才能不加:
```javascript
(singleParam) => { statements }
singleParam => { statements }
```
* 把key這個參數傳入加入這個事件...等更懂在加上細節說明

那其他的就沒什麼，一樣把window這個EventTarget加上keydown這個Eventtype，然後讀到"keycode"去放音樂跟執行css效果。

上述是原本作品的解釋，其實我自己改了一個鋼琴圖跟抓了Do Re Mi Fa Sol的音效來模擬鋼琴的效果XD，也支援滑鼠點案的而不只是讀鍵盤。

這個系列主角還是js，之後會再回頭繼續補充每一個項目的想法跟詳解，而不是解決了問題就算了
然後markdown語法也還不熟悉...所以就先到這。 