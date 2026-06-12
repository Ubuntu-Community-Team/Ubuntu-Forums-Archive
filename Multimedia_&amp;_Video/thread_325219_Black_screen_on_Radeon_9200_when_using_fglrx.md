---
title: "Black screen on Radeon 9200 when using fglrx"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by ernstblaauw on 2006-12-25
I have a 32-bit Edgy Eft installation, on a AMD64 3000+ with a Radeon 9200. I like to use the 'fglrx'-driver (the one ATI made), and of course the version included with Edgy Eft. There are newer versions, but the don't work on such old cards.
I installed the driver using [this](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide), and later using [this](http://ubuntuforums.org/showthread.php?t=24557) method. Both have the same problem: I get a black screen when the log in screen should have come up. It is not crashing, however: I can hear the drums of an initializing Ubuntu. 
I use the DVI output of my Radeon to connect my screen to it. 

Some solutions I found but did not work/don't know how to apply:
[LIST][*]A workaround posted [here](http://wiki.cchtml.com/index.php/Talk:Troubleshooting) is to disable the framebuffer. I actually don't know how to do that
[*]I had to add ```
Option		"MonitorLayout"	"LVDS, TMDS"
``` to the device section of my xorg.conf. That did not work also.
[*]I should add some setting using '[Modelines](http://www.ubuntuforums.org/showpost.php?p=957825&postcount=4)' to my xorg.conf. However, I don't know where and how, and the [source of this solution](http://www.x1000forums.com/index.php?showtopic=5073) does not exist anymore.[/LIST]

I hope you can help me, because I don't know what to do next to get my Radeon 9200 using the fglrx-driver. If you want, I can post my (not working) xorg.conf. 
With regards

---

### Post by iGama on 2006-12-25
I also have a 9200, but the fglrx version on Edgy does _not_ support that card anymore, that is why it is recommend to use the OpenSource Radeon driver, that gives full 3D acceleration. 

The modelines are only necessary on some laptops.

But if u still want to use the fglrx driver, you have to do this after you install the fglrx:

```
wget http://www.guiaubuntupt.org/files/libGL.so.1.2

sudo cp libGL.so.1.2 /usr/lib/libGL.so.1.2
```

This libGL.so.1.2 is the last version where the 9200 and below were suported, so it should work.

Hope it works.

( The file is hosted in my page, so it should be there for a good time :) )

---

### Post by ernstblaauw on 2006-12-25
> **iGama said:**
> I also have a 9200, but the fglrx version on Edgy does _not_ support that card anymore, that is why it is recommend to use the OpenSource Radeon driver, that gives full 3D acceleration. 

The modelines are only necessary on some laptops.

But if u still want to use the fglrx driver, you have to do this after you install the fglrx:

```
wget http://www.guiaubuntupt.org/files/libGL.so.1.2

sudo cp libGL.so.1.2 /usr/lib/libGL.so.1.2
```

This libGL.so.1.2 is the last version where the 9200 and below were suported, so it should work.

Hope it works.

( The file is hosted in my page, so it should be there for a good time :) )

I know it is recommend to use the Open Source driver, and I'm actually using that one atm. However, 'fglrx' is a lot faster than the Open Source driver, and therefore I'm (still) trying to use 'fglrx'.
I tried your suggestion of replacing my libGL with your version. However, I didn't work: I still got a black screen when there should be a screen for logging in.
Thanks for your help! Do you maybe got another hint, because you got the same card?
With regards,
Ernst

PS Do you know how I get my old libGL back? I actually forgot to backup the old one.

---

### Post by iGama on 2006-12-25
you should reinstall :s

If you have a laptop, search for your laptop in the forum, in some situations there is a need to add this line to de xorg.conf in the device section:

Option "MonitorLayout" "LVDS,TMDS"

Good luck

---

### Post by ernstblaauw on 2006-12-27
> **iGama said:**
> you should reinstall :s

If you have a laptop, search for your laptop in the forum, in some situations there is a need to add this line to de xorg.conf in the device section:

Option "MonitorLayout" "LVDS,TMDS"

Good luck

Actually, I don't have a laptop. However, I tried your suggested solution, but it did not change anything: I get a black screen when the log in screen should have come up.

Do you got another tip for me? Or has someone else one?

With regards,
Ernst

---

### Post by ernstblaauw on 2006-12-28
*bump*

---

### Post by iGama on 2006-12-30
No sorry i dont :\

i just dont use fglrx just radeon so i dont know what to say more :S

---

### Post by Dropknee on 2007-01-31
Have the same problem with the drivers 8.28.8, I cant upgrade to the latest drivers because of the Overheating, Crazy Fan bug (X800,X850 have this bug with the latest drivers). the fglrx repo drivers dont have this issue (8.28.8) however I got this black screen bug too when I try to log out, restart , switch user , etc. I cant really figured out how to fix this.

I need help here pls.

---

