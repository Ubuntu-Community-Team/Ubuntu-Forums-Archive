---
title: "DVI on ATI Radeon 9200"
date: 2006-11-09
forum: Multimedia &amp; Video
---

### Post by Goliash on 2006-11-09
I bought a new LCD monitor BenQ FP92W. It has a resolution 1440x900. I plugged into VGA port a it worked. But when I plug it into DVI port it work until KDE starts. When KDE starts, monitor turns off. If I switch cabel to VGA, it works.

Does anyone have working LCD in DVI on Radeon 9200? 

#fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9250/9200 Series DDR Generic
OpenGL version string: 1.3.1091 (X4.3.0-8.28.8)

Should I change anything in xorg.conf?

---

### Post by blackpaw on 2006-11-13
hi.

I have the same card and used a samsung with exactly this resolution and DVI.
Did you follow [this]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide") guide?
It did the trick for me. 

b.

---

### Post by Goliash on 2006-11-13
Thanks for answering. 

I did everything according to this How-to. Everything is working like 3D acceleration but DVI not. Can you post here your Xorg.conf?

Mine is here:

---

### Post by stenka on 2006-12-23
Exactly the same problem with me... I think I tried avery thing.

---

### Post by Goliash on 2006-12-24
That's a pity. It seems there's no solution. Only changing VGA card :(

---

