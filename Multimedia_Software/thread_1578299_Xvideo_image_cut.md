---
title: "Xvideo image cut"
date: 2010-09-20
forum: Multimedia Software
---

### Post by gaga666 on 2010-09-20
Hi all,
I'm running ubuntu 10.04 with all default settings. I have dual-head ATI Radeon 9600 video card with two monitors attached: 1280x1024 and 1920x1080. Therefore, I wrote "virtual 3200x1080" in "Screen" section of xorg.conf. Two enable both monitors I use 
```

xrandr --output DVI-0 --right-of VGA-0 --mode 1920x1080 --primary

```
and this works fine. But when I try to play video with any player(vlc, mplayer, totem), I can neither drag it to the right sight of the big monitor nor make it fullscreen: it seems to be cut on the border of smaller screen(1280 px). So the rightmost part of the screen is simply filled with garbage. On left(smaller) monitor everithing is fine.
If I choose not xv but gl output driver for mplayer, everything is fine, but performance is not so good.
There was no such problem in Mint8. Any suggestions?

---

### Post by gaga666 on 2010-09-20
Forgot to mention, that disabling compiz didn't help. Xorg.0.log doesn't show anything strange as well.

---

### Post by gaga666 on 2010-09-21
And finally one more bump

---

### Post by gaga666 on 2010-09-22
Ok, I've found the reason: KMS.  I have old Radeon9600 video card and glxgears gave me about 3400 fps in Mint8. I noticed that in ubuntu10.04 it's only 500. So I disabled KMS by adding 'nomodeset' to grub boot options and vuala: I have 2800 fps in glxgears and fine full-screen video via xv driver on both monitors. 20% performance degradation in glxgears is bad, but it may be not KMS-related, since there are a lot of unneccessary **** booted by default. Thanks everyone for your attention. PS where to write bug report on this?

---

### Post by RubeSam on 2010-09-22
If you make a rectangular selection around the image and then copy it  you can then go to "file" and "new" and it says something like "new  image from clipboard"...not looking at the program, computer already  running too slow right now..
Anyway,  the image will come up when you select the "new image from clipboard" option.
You can then save it as a jpeg and paste it in a word doc. There shouldn't be a box.

---

