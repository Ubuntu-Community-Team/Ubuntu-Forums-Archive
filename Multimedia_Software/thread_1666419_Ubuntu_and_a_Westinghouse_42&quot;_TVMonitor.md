---
title: "Ubuntu and a Westinghouse 42&quot; TV/Monitor"
date: 2011-01-13
forum: Multimedia Software
---

### Post by irv on 2011-01-13
I got a nice Christmas gift, a Westinghouse 42" TV/Monitor, and it works great with Ubuntu 10.10. The one problem I have is watching Hulu movies on it. When I go to full screen mode, the digital image slows and get blocky. When I check the settings, it is telling me I have a 32" not a 42" and there is no way to change it. It does tell me I have a Westinghouse. I also have a Roku and I believe it has a Linux OS on it and it works great. If I run Hulu out of Win7 it also works great. Does anyone have any ideas on what I can try?
Thanks for the help.

---

### Post by tjones00 on 2011-01-13
From your postcount I assume you're an relatively experienced Ubuntu/Linux user.

From your description of the issue I assume a nvidia card in your pc. What card do you have?

If nvidia do you have hardware acceleration enabled (vdpau)? and the latest flash?

Did your nvidia driver get a proper EDID from the tv? This seems to be an issue especially with nvidia recently. Check the Xorg.0.log.

---

### Post by irv on 2011-01-13
> **tjones00 said:**
> From your postcount I assume you're an relatively experienced Ubuntu/Linux user.

From your description of the issue I assume a nvidia card in your pc. What card do you have?

If nvidia do you have hardware acceleration enabled (vdpau)? and the latest flash?

Did your nvidia driver get a proper EDID from the tv? This seems to be an issue especially with nvidia recently. Check the Xorg.0.log.

First I don't have a nvidia card in my laptop. I have a Dell Inspiron 1521 and I believe I have a Radeon Xpress video card installed. Also I have 10.1.102.65ubuntu0.10.10.1 (flashplugin-installer). Hope this info helps.

---

### Post by tjones00 on 2011-01-13
Ah unfortunately I don't know anything about ATI hardware acceleration. It still seems like your having an EDID issue though if your screen is not identified properly.

The radeon Xpress series is an older card that has been getting a lot of attention recently.

[http://ubuntuforums.org/showthread.php?t=1656791](http://ubuntuforums.org/showthread.php?t=1656791)
[http://ubuntuforums.org/showthread.php?t=1665001](http://ubuntuforums.org/showthread.php?t=1665001)


[http://www.dell.com/us/en/dfh/notebooks/inspnnb_152x/pd.aspx?refid=inspnnb_152x&cs=22&s=dfh](http://www.dell.com/us/en/dfh/notebooks/inspnnb_152x/pd.aspx?refid=inspnnb_152x&cs=22&s=dfh)

from the above link

> **AMD Graphics Options**
Integrated ATI Radeon Xpress 1270 with HyperMemoryTM   										(64MB dedicated local frame buffer) 									


---

### Post by irv on 2011-01-13
Thank for the links. I guess this is no real issue seeing I have a Roku and Win7 for the Hulu and Netflix. I will play around with the issue but if I don't come up with an answer for now it won't be the end of the world.
Thanks again.

---

