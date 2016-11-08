misaki-json
===========

# なにこれ
美咲フォント( http://www.geocities.jp/littlimi/misaki.htm )を、プログラミングで使いやすいように JSON 化したものです。

# 内容物
- misaki.json
  - UTF-8 文字を key にした辞書形式
  - 行ごとに、列のビットを数値化したもの

- misaki-num.json
  - key を コード化したUTF-8 文字に変更
  - python 用


# つかいかた

- Nodejs

```javascript
'use strict';

const misaki = require("./misaki.json");

const toBitmap = arr => {
  return arr.map(bin => {
    let r = [];
    for(let i = 0;i < 8;i++){
      r[7 - i] = bin & 1 << i ? 1 : 0;
    }
    return r;
  });
};

const bitmap = toBitmap(misaki["あ"]);

for(let y = 0;y < 8;y++){
  for(let x = 0;x < 8;x++){
    process.stdout.write(bitmap[y][x] ? "##" : "  ");
  }
  console.log();
}
```


```
.
    ##
  ##########
    ##
    ########
  ####  ##  ##
##  ####    ##
  ####    ##
```


# めも
- 半角英数字は無理、全角英数字に変換する必要あり
