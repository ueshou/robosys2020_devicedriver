# robosys2020_devicedriver
ロボットシステム学演習　デバイスドライバ

---
##  実装内容

今回は、ロボットシステム学第7回、8回授業の際、上田先生が作成したデバイスドライバ(https://github.com/ryuichiueda/robosys_device_drivers/blob/master/myled.c)　に変更を加えて作成しています。  
・gを入力すると緑のLEDが2つ点灯します。  
・sを入力するとまず1つの緑のLEDが6回点滅、その後緑のLEDが消え黄色が点灯する。その後黄色が消え赤が点灯する。  
・eを入力するとすべてのLEDが消える。  

---
## 用意するもの

・Raspberry Pi 4 Model8  
・ブレッドボード  
・LED（緑）×2  
・LED（赤）×2  
・LED（黄色）  
・ジャンパー線　オス-メス　×5  
・ジャンパー線　オス-オス　×6  
・抵抗　330Ω　×4  

---

## 回路

以下のような回路を組み、使用しました。  

<img src = https://user-images.githubusercontent.com/53548215/102705889-c07ccd00-42cf-11eb-8b72-c31cc7345b4d.jpeg width = 500px />

・LED(黄色)の隣のLED(緑)をGPIO 25  
・LED(赤)の隣のLED(緑)をGPIO 22  
・LED(黄色)をGPIO 27  
・二つのLED(赤)をGPIO 23  
へそれぞれつなぎます。GNDはどのピンからとってもかまいません。

---

## ビルド

実行する前に、以下のコマンドを入力してビルドしてください。

```sh
$ git clone https://github.com/ueshou/robosys2020_devicedriver.git
$ cd robosys2020_devicedriver/myled
$ make
$ sudo insmod myled.ko
$ sudo chmod 666 /dev/myled0
```

---

## 実行結果
### gを入力したとき

```sh
$ echo g > /dev/myled0
```

上記のように'g'を入力すると、二つのLED(緑)が点灯します

---

### sを入力したとき

```sh
$ echo s > /dev/myled0
```
上記のように's'を入力すると、次のように動作します。
1.一つのLED(緑)が6回点滅  
2.2つのLED(緑)が消え、LED(黄)が点灯  
3.LED(黄)が消え、LED(赤)が点灯  

---

### eを入力したとき

```sh
$ echo e > /dev/myled0
```
上記のようにeを入力するとすべてのLEDが消えます。

---

## デモ動画
youtubeにアップロードした動画は下記の通りになります。

## ライセンス


