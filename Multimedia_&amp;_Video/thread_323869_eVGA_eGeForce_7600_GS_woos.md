---
title: "eVGA eGeForce 7600 GS woos"
date: 2006-12-22
forum: Multimedia &amp; Video
---

### Post by skaramanger on 2006-12-22
Greetings,

I was unsuccessful searching  for posts that might address the problem I am having, so here goes.  On an impulse buy (Circuit City was the benefactor) I purchased the above named agp video card. I installed it and booted into 'safe mode' and attempted to  configure xorg to recognize my new card.  Well no go.  I tried:

dpkg-reconfigure nvidia-glx nvidia-kernel-common 

and 

dpkg-reconfigure xorg-server

I have gone from the system not finding a screen to init 3, login, startx  and the screen goes blank and to sleep <cntl><alt><sysrq>(r,s,e,i,u) to restart system.

Apparently, my mobo is not recognizing the new card, properly.  I've read a posting or 2 that discusses installing the nvidia beta driver.  I'm currently booted using a livecd to compose this message.

Any suggestions?

TIA,

Skaramanger

---

### Post by taurus on 2006-12-22
It should be

```
dpkg-reconfigure xserver-xorg
startx
```

---

### Post by tseliot on 2006-12-23
Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine


NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

Then you might want to install the Nvidia driver:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by skaramanger on 2006-12-23
> **tseliot said:**
> Boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

Type:
```
reboot
```

On next reboot the Xserver should work fine



NOTE: if the problem is not solved try using "vga" instead of "vesa" and try again.

Then you might want to install the Nvidia driver:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

Thanks tseliot and taurus.  Upon seeing your replies, I realized how much info was missing from my initial post.  I'm replacing my GeForce4 MX 4000 8x AGP card with an e-Force 7600 GS 8x AGP card.  I currently have the latest nvidia-glx & nvidia-kernel-common installed.  I thought that by reinstalling/reconfiguring the nvidia packages and reconfiguring xserver, the new card would be recognized by X.  But,  that is not the case.  The system recognizes that it is an nvidia based card, but doesn't recognize the memory chips.  I'm going to at the links you provided tseliot.  Post my findings.

Skaramanger

---

### Post by skaramanger on 2006-12-23
tseliot,

I'm trying your method using enyv.
I uninstalled:
nvidia-glx, nvidia-kernel-common, linux-image-restricted-`uname -r`. After running envy, and starting X, I got the same black screen.  So, I'm going to attach some more system info.

skaramanger

<CODE>uname -r</CODE> 2.6.15-27-k7
FIC AU13 mobo AMD Athlon 2700 1GB Ram
eVGA eGeForce 7600 GS 8X AGP

---

