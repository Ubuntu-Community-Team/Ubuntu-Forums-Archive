---
title: "ATi DRI failed to initialize"
date: 2006-12-13
forum: Multimedia &amp; Video
---

### Post by AquaFox90 on 2006-12-13
I am using Edgy. Linux 2.6.17 generic.

This is my Xorg.0.log:
[http://rafb.net/paste/results/xe7jmn14.html](http://rafb.net/paste/results/xe7jmn14.html)

My xorg.conf:
[http://rafb.net/paste/results/Wv3uxB58.html](http://rafb.net/paste/results/Wv3uxB58.html)

RAFB PASTES GET DELETED IN 24 HOURS :(.
```
qusai@ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

```
Please help. I got fglrx from the repo 8.28.8

---

### Post by wenzlicker on 2006-12-13
I had the same problem. I fixed it by adding this to my xorg.conf file.

```

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

After looking at yours, I noticed you had it in there. Just out of curiosity, what graphics card do you have? Also, what happens when you hit ctrl+alt+f1?

---

### Post by AquaFox90 on 2006-12-13
I have a Radeon 9200 SE. When I hit Crtl+ ALt+ F1 I go to tty1.

---

### Post by wenzlicker on 2006-12-13
Okay, thanks.

I have a X1400. When I type ctrl+alt+f1, I get a garbled screen (lots of lines and colors). The only tty that works is tty7 (xorg)

---

