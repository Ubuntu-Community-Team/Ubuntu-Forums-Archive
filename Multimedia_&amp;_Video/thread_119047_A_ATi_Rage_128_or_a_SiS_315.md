---
title: "A ATi Rage 128 or a SiS 315?"
date: 2006-01-18
forum: Multimedia &amp; Video
---

### Post by Sputnik_RU on 2006-01-18
I'm building a computer only to be used for running linux. I got two old videocards in my closet, but I really don't know wich one I should build in. What would be the best card to use, considering 2d quality and accleration for the interface (I use both Gnome and KDE). I also heard the new X.Org versions will use OpenGL acceleration, wich card will be best for that?

**The system:**
AMD Athlon XP 1700+
256 MB DDR266
[Elitegroup K7VTA3 (VIA KT266A)](http://www.ecs.com.tw/ECSWeb/Products/ProductsDetail.aspx?MenuID=26&LanID=9&DetailID=184&DetailName=Specification)
Maxtor D740X-6L 40GB
[D-Link DFE-530TX+ (VIA Rhine III)](http://www.dlink.com/products/?pid=122)

**The videocards:**
1) [ATi Rage 128 Pro, with 32 MB memory. The brand is Gigabyte (type: GV-AG32S).](http://www.gigabyte.com.tw/VGA/Products/Products_GV-AG32S.htm)
2) [SiS 315, with 64 MB memory. The brand is Elitegroup (type: AG315T-64).](http://www.neoseeker.com/Hardware/Products/ECS_SiS315AGP/)

---

### Post by az on 2006-01-18
[http://www.winischhofer.at/linuxsispart1.shtml#12](http://www.winischhofer.at/linuxsispart1.shtml#12)

Quote:
"# DRI is only supported on the 300 series (300/305, 630, 730). A DRI driver for the SiS 300 series is provided by XFree86 4.1, 4.2(.1), XFree86 4.4 and X.org 6.7.0 and later. XFree86 4.3 does not contain a SiS DRI driver; However, installing the drivers from 4.2(.1) works well.
# Once again: There is no DRI/OpenGL/3D support for the SiS 6326, 5597/5598, 530/620, 315, 550, 650, 651, 740, 330, 661, 741, 760, 761 including all model variations with letters in the model number."



And from my ATI card (32 megs of ram):
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

glxgears -printfps
3961 frames in 5.0 seconds = 792.066 FPS
3320 frames in 5.0 seconds = 663.860 FPS
3319 frames in 5.0 seconds = 663.635 FPS



The caveat is that at the highest resolution and color depth (default for Ubuntu) dri suffers.  I have to set a lower resolution and color depth to prevent memopry from being allocated to 2D.  I get much better performance by doing this.

---

### Post by Sputnik_RU on 2006-01-18
[QUOTE=azz]The caveat is that at the highest resolution and color depth (default for Ubuntu) dri suffers.  I have to set a lower resolution and color depth to prevent memopry from being allocated to 2D.  I get much better performance by doing this.[/QUOTE]
I understand the ATi card is the better option right? The thing I quoted is not really clear to me. But I can run a 1024x768 resolution with 24bits color right (sorry if I misunderstood).

---

### Post by az on 2006-01-18
Out of the two, the ATI card is better because the SIS one does not have 3D support in linux.

Blame the manufacturer.

---

### Post by Sputnik_RU on 2006-01-18
@azz
Thanks for your help. I'm putting the ATi card in right now.

---

