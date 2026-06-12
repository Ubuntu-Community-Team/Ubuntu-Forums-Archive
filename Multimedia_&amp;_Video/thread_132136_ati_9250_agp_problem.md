---
title: "ati 9250 agp problem"
date: 2006-02-17
forum: Multimedia &amp; Video
---

### Post by shooks on 2006-02-17
hi i'm new here. and sorry about the bad english, but i alread tried on my language forum and couldn't get a reply.

i followed all the instructions from [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) but when it's all done i get a screen too bright! i open the ati control in the applications menu, and try to change the gamma sliders but it is still too bright!

does anybody have any ideia?

thank you

---

### Post by vruum on 2006-02-17
do you have a tv connected? if so try typing
```
sudo aticonfig --desktop-setup=mirror
``` 
and then either restart or type
```
 sudo /etc/init.d/gdm restart
```
if you don't have a tv connected could you say a little more about your setup? or post your /etc/X11/xorg.conf file?

---

### Post by sevencapitalsins on 2006-03-19
Here I tried the same thing, but I was less lucky than you. The screen is black!

I had to reboot, enter with the "recovery mode", and modify the xorg.conf file with vi. I had to restore the "ati" driver instead of fgrlx.

Tomorrow I'll go and buy an nvidia card!!!!

It's only my personal opinion, but i don't think that the 9250 is supported by the fgrlx. I didn't find it in the release notes provided by ati, there's only a "9200 series" but no "9250 series".

---

### Post by iramhernandez on 2006-12-19
Newer versions of fglrx do not support the 9250.

---

### Post by sevencapitalsins on 2006-12-19
As i thought.

Sold the ATI 9250, bought nVidia 5500fx, works fine. Thanks to all. happy new year!

---

