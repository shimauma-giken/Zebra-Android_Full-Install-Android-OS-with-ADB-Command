## Zebra-Android_Full Install Android OS with ADB Command
## Adb コマンドを用いてAndroid OS をフルインストールする

本ガイドはWindows 11 を前提に手順を説明する。他OSをお使いの場合は該当OSのReference ガイドを確認すること。

### 参考
Android端末のOSアップデート  </br>
https://supportcommunity.zebra.com/s/article/Updating-OS-on-an-Android-Device?language=ja
<br>
<br>

### 事前準備
下記を確認・入手しておくこと。

1. 現在のOSバージョン
2. 新規インストールOSのFull Updateファイル
3. PCにadbツールがインストールされていること
4. Zebra Android 端末が開発者モードになっていること
5. PC <--> Zebra Android 接続ケーブル 

<br>
<br>

### ガイド

1. PC <--> Android 端末をUSB接続する
2. コマンドラインから接続確認をする
   
    ```
    C:\Users\xxxxxx>adb devices
    List of devices attached
    22263524700656  device
    ```
    <br>


3. Android端末をリカバリモードにする。
    ```
    C:\Users\xxxxxx>adb reboot recovery
    ```
    <br>


4. Android端末の液晶メニューを操作し、下記いずれかを選択する。

    - Apply Upgrade from ADB
    - Apply Downgrade from ADB

    `※ 端末OSと同じバージョンをインストールする場合はUpgradeを選択すること。` </br>
    `※ 誤った選択をした場合はエラーとなり、処理は中断するので注意。`
    <br>
    

5. adb sideload コマンドを用いてインストールを開始する。
    ```
    C:\Users\xxxxxx\Downloads\ET45>dir
    Volume in drive C has no label.
    Volume Serial Number is 261D-CA0F

    Directory of C:\Users\xxxxxx\Downloads\ET45

    2024/05/18  19:10    <DIR>          .
    2024/05/18  19:10    <DIR>          ..
    2024/05/17  15:48     2,249,877,386 GO_FULL_UPDATE_13-28-24.00-TG-U00-STD-GSE-04.zip
                1 File(s)  2,249,877,386 bytes
                2 Dir(s)  457,634,787,328 bytes free

    C:\Users\xxxxxx\Downloads\ET45>adb sideload GO_FULL_UPDATE_13-28-24.00-TG-U00-STD-GSE-04.zip
    ```
    <br>

6. Android 端末のリカバリー画面に下記メッセージがあることを確認する。
   ```
   Installing SUCCESS....

   Install from ADB complete. 
   ```

7. Android 端末を再起動。
   <br>



8. OSの更新確認をする。
   
   ```
   C:\Users\xxxxxx\Downloads\ET45>adb shell getprop ro.build.id
    13-28-24.00-TG-U00-STD-GSE-04
    ```