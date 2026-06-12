---
title: "Getting Flash to work"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by malfist on 2007-03-11
I just recently installed flashplugin-nonfree and flash still isn't working. I may have other packages (like flash-firefox (or something like that)) installed. I'vew never really got flash to work.

I did what the wiki said and it doesn't work. (I've checked at youtube, and other places).

---

### Post by r4ik on 2007-03-11
Try,

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Should work.

---

### Post by malfist on 2007-03-11
Nope still doesn't, for either process. I did restart the browser each time.
terminal show this (I launched firefox from it):
```

NP_Initialize
New
SetWindow
SetWindow
NewStream
WriteReady
Write
decoding...
New block
DestroyStream
Destroy
NP_Shutdown

```
after visiting youtube

---

### Post by r4ik on 2007-03-11
Did you include this,

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

from the post ?

---

### Post by malfist on 2007-03-11
still doesn't work. I'm using Firefox 1.5, not 2

---

### Post by r4ik on 2007-03-12
Take a look at,

[http://www.getautomatix.com/](http://www.getautomatix.com/)

everything,well almost, is there.

---

### Post by malfist on 2007-03-14
I also get some strange event when firefox tries to load flash, keyboard stops working on browser or lagges really bad, sometimes into other programs. I'll check out automatix

---

### Post by malfist on 2007-03-14
It seems that website isn't working.

---

### Post by r4ik on 2007-03-14
Oke try,

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Should work.

---

### Post by malfist on 2007-03-14
How do I donwload it,  Ican't find it in my list of programs and it doesn't provide a link.

---

### Post by r4ik on 2007-03-15
[http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html)

Put,

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

in a terminal and hit enter,

download here,

[http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb](http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb)

---

### Post by malfist on 2007-03-16
option for flash is greyed out, even when Irun easyubuntu with sudo

---

### Post by malfist on 2007-03-17
automatrix is throwing error when I try to load it, something about all keys could not be found and in the command line it shows a 404 error. I followed the instructions in the wiki and found out I have 6.06 instead of 6.10 (I could have swore I had 6.10) so I donwloaded the wrong keys first, could that be a problem?

---

