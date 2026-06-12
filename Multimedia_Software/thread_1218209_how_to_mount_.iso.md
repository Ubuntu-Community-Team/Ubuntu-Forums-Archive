---
title: "how to mount .iso?"
date: 2009-07-20
forum: Multimedia Software
---

### Post by jordanoff11121 on 2009-07-20
hello guys!
how to mount .iso? pls tell me step by step?
i have ubuntu 9.01 or something like that .//

---

### Post by tomd123 on 2009-07-20
[http://www.google.com/search?hl=en&client=firefox-a&channel=s&rls=org.mozilla%3Aen-US%3Aofficial&hs=Xvv&q=how+to+mount+iso+ubuntu&aq=f&oq=&aqi=g1](http://www.google.com/search?hl=en&client=firefox-a&channel=s&rls=org.mozilla%3Aen-US%3Aofficial&hs=Xvv&q=how+to+mount+iso+ubuntu&aq=f&oq=&aqi=g1)

---

### Post by Keith Hedger on 2009-07-20
Try:
```
mkdir /tmp/iso
sudo mount -o loop "ubuntu-8.10-alternate-amd64.iso" /tmp/iso
```

Of couse you should change the name of the iso to suit yourself and use a fullpath if you are not in the same dir as the iso

---

### Post by igorzwx on 2009-07-20
On my Ubuntu 9.04,
if I click on ISO, it is mounted automatically.
Perhaps, a plug for nautilus should be installed.
Other usefull plugs: "open in terminal", etc.

---

### Post by Grishka on 2009-07-20
[apt://gisomount](apt://gisomount).

---

### Post by igorzwx on 2009-07-20
Hi Grishka!

Has Koala pulseaudio installed by default?

---

### Post by igorzwx on 2009-07-20
**[The Silent Number: 13 things to get excited for in *Ubuntu* 9.10 [B]...**]("http://blog.thesilentnumber.me/2009/06/13-things-to-get-excited-for-in-ubuntu.html")[/B]

13 things to get excited for in *Ubuntu* 9.10 Karmic *Koala* **.....** work and not to forget the loved *pulse* audio which is now "perfect" but broke sound on *Ubuntu* **...**
blog.thesilentnumber.me/.../13-things-to-get-excited-for-in-**ubuntu**.html - [Cached]("http://209.85.135.132/search?q=cache:R3s1r4qxS5YJ:blog.thesilentnumber.me/2009/06/13-things-to-get-excited-for-in-ubuntu.html+ubuntu+koala+pulse&cd=10&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:blog.thesilentnumber.me/2009/06/13-things-to-get-excited-for-in-ubuntu.html")

---

