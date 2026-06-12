---
title: "Remote Control Ubuntu from Android Phone"
date: 2012-01-07
forum: Multimedia Software
---

### Post by zulu99 on 2012-01-07
From today for free you can control your Ubuntu with your android phone.

DroidMote Client
[https://market.android.com/details?id=org.videomap.droidmoteclient]("http://www.youtube.com/redirect?q=https%3A%2F%2Fmarket.android.com%2Fdetails%3Fid%3Dorg.videomap.droidmoteclient&session_token=qAkZLgeSBfR3CRxrT6vgy3cEaWJ8MTMyNjA0NDUyNEAxMzI1OTU4MTI0")

- DroidMote Server for Linux 1.0
[http://www.megaupload.com/?d=CYAHRGHN]("http://www.youtube.com/redirect?q=http%3A%2F%2Fwww.megaupload.com%2F%3Fd%3DCYAHRGHN&session_token=qAkZLgeSBfR3CRxrT6vgy3cEaWJ8MTMyNjA0NDUyNEAxMzI1OTU4MTI0")

Video:
[http://www.youtube.com/watch?v=Vksq4jN3n2M](http://www.youtube.com/watch?v=Vksq4jN3n2M)

---

### Post by Dr.Aequitas on 2012-01-12
hey zulu. i have downloaded the file droidmote server for linux. i did the chmod 777 thing and run it this way
```
sudo ./droidmote 2302 qwerty
```
but then nothing happens. no droidmote server window, no start button.. nothing.. just this:
```
aequitas@Aequitas:~/&#304;ndirilenler$ sudo ./droidmote 2302 qwerty


```

is there something wrong?

I have solved the issue. 
You need to set the exact same IP addresses for both android device and the linux machine.
For example, you are connected to a wireless router and your linux machine's IP is 192.168.1.15 then you have to set this IP to the droidmote client on android device. That's where I got stuck.

By the way I really like your application. Congratulations and good luck on Windows version. If you need translations for Turkish, I'll gladly help you on this.

---

