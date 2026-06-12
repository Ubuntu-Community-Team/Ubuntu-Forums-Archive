---
title: "asio4all"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by tubunu on 2008-01-12
I would like to install asio drivers on Ubuntu. However, asio4all doesn't seem to be working under wine. Are there any alternatives? I tried wineasio, but I can't get it to compile... it says I need asio.h file, but I don't know where to get it from? :confused:

---

### Post by tubunu on 2008-01-12
OK, here's a nice tutorial:
[http://www.sandgreen.dk/xt2/wineasio.html](http://www.sandgreen.dk/xt2/wineasio.html)

You basically need to run:
```
sudo apt-get -y install wine wine-dev libjack0.100.0-dev qjackctl build-essential
```

Copy **wineasio.dll.so** and paste it to /usr/lib/wine

Then:

```
regsvr32 wineasio.dll
```
and
```
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so.0
```

:guitar:

---

