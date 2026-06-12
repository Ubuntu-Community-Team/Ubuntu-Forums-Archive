---
title: "Can't get 1080p at higher refresh rates (intrepid + ati)"
date: 2009-02-16
forum: Multimedia Software
---

### Post by rsmallri on 2009-02-16
Hi,
I have just got a pioneer 1080p plasma screen and a home theatre pc which connects to the screen via hdmi. While everything else works pretty well, I cannot get 1080p to display at 50 or 60Hz, only 24, 25 and 30. When I try to increase the refresh in the ATI control panel (amdcccle) the screen goes blank and then eventually reverts to a lower res/refresh if I don't press OK. Interestingly, during POST and the Ubuntu loading screen the image is displayed on the screen and is identified as being 1080p. Plugging in my 24" monitor via DVI confirms a resolution of 1920 x 1080 @ 50Hz. To me this says that there is an issue with the ATI driver or X configuration, as it appears to work at the desired resolution prior to X starting. 

I had originally suspected it may be a cable throughput issue as low resolutions work with high refreshes and high resolutions work with low ones however I have tried 2 cables. As both cables were less than 2m and 1080p 8-bit is not very taxing in the scheme of hdmi I no longer believe this to be the issue.

My motherboard is an Asus M3a78-EM (780G chipset) with an onboard Radeon HD 3200 that I am using as the display adapter. The latest version of the proprietary ati drivers are installed:
```
ryan@media-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3200 Graphics
OpenGL version string: 2.1.8395 Release

```

I have tried a number of variations in xorg.conf. The current one I am using is just the template which has been modified by using aticonfig --initial. I explicitly added a few modes, 720p being first, so that I could see the gnome login screen.

It doesn't seem as though it's an issue with correctly identifying the panel's modes as both the ATI utility and X (via Xorg.0.log) seem perfectly capable of identifying its resolutions and refresh rates... the screen just goes blank when I try to change in to higher res/refresh modes.

The PC is the only 1080p capable device I have atm but I will try to borrow another one to prove where the problem lies. In the meantime I am out of ideas so if anyone has any proposed solutions or diagnostic measures that would be good. I have attached my current xorg.conf and the one that I was using previously, both with the same results. Here is the pastebin link for my Xorg.0.log file: [Xorg.0.log](http://pastebin.com/f343c0409)

If X was refusing to enter the new mode then I would know how to get more information and identify the problem, but afaik X thinks it has successfully entered the new resolution... I have no idea how to proceed.

---

### Post by rsmallri on 2009-02-18
bump

---

### Post by alejandro.mc on 2009-02-19
Nice thread.

Could use some help too.

Bye!

---

### Post by rsmallri on 2009-02-19
I plugged the PC into a 30" Dell monitor via HDMI and it was capable of doing 1080p @ 60Hz. This says to me that the drivers are somehow getting the wrong information from my TV. It should be noted that the Dell is capable of 2560 x 1600 i.e. I was not driving it at it's maximum resolution, whereas with the TV I am (trying to).

---

