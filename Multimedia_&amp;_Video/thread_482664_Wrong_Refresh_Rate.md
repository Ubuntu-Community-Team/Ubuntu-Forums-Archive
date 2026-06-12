---
title: "Wrong Refresh Rate"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by Dark Aspect on 2007-06-23
After I upgraded my Ubuntu 6.10 to Ubuntu 7.04 my refresh rate was the same 60 Hz its been at but when I installed my Nvidia Driver my highest refresh rate is 58 hz.And after I play some games like Doom 3 it goes as low as 50 hz.I have tried to reconfigure my video X server with this command:

sudo dpkg-reconfigure xserver-xorg

But this fails it goes up to 90 Hz but when I reset my system its highest setting is 58 Hz again.Is there a way I can keep my refresh rate at 60 Hz and install the Nvidia driver.I have a GeForce 6800 GS PCI-E video card.Thanks for any advice.

---

### Post by Biased turkey on 2007-06-23
I'm sorry I can't help because I have a similar problem, see that thread:
[http://ubuntuforums.org/showthread.php?t=476966]("http://ubuntuforums.org/showthread.php?t=476966")

We are in the same ( sinking ) boat  :(

---

### Post by nutz on 2007-06-23
[http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline)

---

### Post by nutz on 2007-06-23
Or if you are using the nvidia driver with an LCD you will probably have better luck with a metamode. Check out my xorg.conf for reference...

```
Section "Monitor"
       Identifier      "Generic Monitor"
       Option          "DPMS"
EndSection

Section "Screen"
       Identifier      "Default Screen"
       Device          "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
       Monitor         "Generic Monitor"
       DefaultDepth    24
       Option         "metamodes" "CRT: 1680x1050_60_0 +0+0"
       SubSection     "Display"
       Depth       24
       Modes      "1680x1050"
   EndSubSection
EndSection

Section "ServerLayout"
       Identifier      "Default Layout"
	screen		"Default Screen"
       Inputdevice     "Generic Keyboard"
       Inputdevice     "Configured Mouse"
       Inputdevice     "Synaptics Touchpad"
EndSection
```

---

### Post by nutz on 2007-06-23
The above metamode fixes my resolution to the native 1680x1050@60hz of my LCD...

---

### Post by Dark Aspect on 2007-06-24
Thanks um this is going to sound stupid but where is the xorg.conf file stored on Ubuntu 7.04.

---

### Post by darkog on 2007-06-24
you should find it in 

/etc/X11/xorg.conf

---

### Post by Dark Aspect on 2007-06-24
> **darkog said:**
> you should find it in 

/etc/X11/xorg.conf
Thanks again the problem is fixed now.

---

### Post by nutz on 2007-06-24
just curious, did you use a metamode or a modeline?

---

### Post by Dark Aspect on 2007-06-24
> **nutz said:**
> just curious, did you use a metamode or a modeline?
I have a LCD so I used the metamode since you said I would have better luck with that on a LCD and it seemed to work.I never tried the modeline because when I checked this thread again you had posted the information about the LCD.Thanks for the info.

---

### Post by darkog on 2007-06-24
f.y.i..  this link has helped me get X working properly.

[http://www.x.org/wiki/FAQVideoModes]("http://www.x.org/wiki/FAQVideoModes")

---

### Post by nutz on 2007-06-24
Glad to hear it. The nvidia drivers ten to do better with metamodes and modelines it seems.

---

