---
title: "fulscreen problems - video playing"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by xmas1 on 2008-01-26
Hello :)

I have one small problem while watching videos on my Ubuntu 7.10. 
The problem is that while I am watching a video (movies) suddenly the screen goes black...and I have to move the mouse, so that the screen will appear again. It's like I have activated the screen saver.

The problem occurs whit any player. (Totem, Kaffeine.. )

Hope I described it well. Any suggestions. Thanks in advanced.

---

### Post by Azyx on 2008-01-26
Have you screensaver activated? tried to deactivate it?

Otherwise Totem is not good player I have really problem with It, espacially when I have propretariay Nvidia-drivers activated. It do bad thing, lika change resolution in full screen and don't change it back. Have not tried Kaffein. The only player I tried and work fine Is VLC.

Azyx


> **xmas1 said:**
> Hello :)

I have one small problem while watching videos on my Ubuntu 7.10. 
The problem is that while I am watching a video (movies) suddenly the screen goes black...and I have to move the mouse, so that the screen will appear again. It's like I have activated the screen saver.

The problem occurs whit any player. (Totem, Kaffeine.. )

Hope I described it well. Any suggestions. Thanks in advanced.

---

### Post by xmas1 on 2008-01-26
Thanks for the reply.

I have tried to deactivate the screen saver...but this doesn't solve the problem. 
Any other suggestions?

---

### Post by adelodder on 2008-01-26
It might be because of the DPMS option (Display Power Management Signaling).

You can disable it by commenting the line out (with **#**) in your xorg.conf (etc/X11/xorg.conf):

Here is a portion of my xorg.conf file:

```
Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"FUS C19-3"
	Horizsync	30.0	-	83.0
	Vertrefresh	55.0	-	76.0
	**#**Option		"DPMS"
EndSection
```

---

### Post by xmas1 on 2008-01-26
I'll try this. But wouldn't that disable the whole power management (turning off the screen when inactive) ? Thanks

---

### Post by adelodder on 2008-01-26
your problem seems similar to the one in this thread:

[http://ubuntuforums.org/archive/index.php/t-121061.html]("http://ubuntuforums.org/archive/index.php/t-121061.html")

---

### Post by xmas1 on 2008-01-26
Thanks for the link. Yes, it's similar. But, the interesting part is that I didn't had similar problems before I reinstalled Ubuntu.

btw...I forgot to mention that I am running Ubuntu on Dell Inspiron 1501 laptop. 

I'll try disabling this an will report later ;)

---

### Post by xmas1 on 2008-01-26
Disabling the DPMS option didn't helped. I still have the same problem :( 
Any other suggestions ?

---

### Post by xmas1 on 2008-01-27
Bump :(

---

