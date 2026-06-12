---
title: "Unable to find 1280 x 1024 resolution"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by Handssolow on 2007-08-07
I've just changed my motherboard and cpu so I guess it was to be expected that I'd have to reconfigure X server. My Syncmaster 940mw has a max resolution of 1440 x 900 though optimal screen is quoted at 1280 x 1024 at 60Hz. Geforce 6600GT is my video card.
Despite selecting 1280 x1024 in X configuration and confirmed later in /etc/X11/xorg.conf it does not appear as an option in either the Nvidia Settings program (Applications>System Tools>Nvidia settings) or in Screen Resolution (System>Preferences>Screen Resolution), 1440 x 900 works though not so acceptable with my vision.

If I omit 1440 x900 in X server configuration it makes no difference, 1280 x1024 still does not appear, why doesn't it appear?

---

### Post by dougfractal on 2007-08-07
use displayconfig-gtk, it is a display config wizard.

sudo apt-get install displayconfig-gtk
sudo displayconfig-gtk


or 

I think your refresh values are

33-81kHz
56-75Hz



but from this thread
[http://ubuntuforums.org/showthread.php?t=516859&highlight=samsung](http://ubuntuforums.org/showthread.php?t=516859&highlight=samsung)
here someone's 1440x900 xorg stuff
[http://ubuntuforums.org/showthread.php?t=280683](http://ubuntuforums.org/showthread.php?t=280683)

```
Section "Monitor"
Identifier "SyncMaster"
VendorName "Samsung" 
ModelName "SyncMaster 940MW" 
HorizSync 33-81
VertRefresh 56-75

# IF THIS DOESN'T WORK REPLACE THIS WITH THE LINES BELOW

#HorizSync 25-100
#VertRefresh 30-90 
Option "DPMS"
#Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection
```

```
Section "Screen"
Identifier "Default Screen"
Device "Default Device"
Monitor "SyncMaster"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1440x864" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1400x864" "1220x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection
```

---

### Post by Handssolow on 2007-08-08
Thanks for your reply dougfractal but I've not made much progress despite working at this for some while. I've got a suspicion that I've posted on this topic before but haven't been able to find the my old reference.

I'm still missing the option for 1280 x1024 in Nvidia Settings and Screen Resolution in Preferences whilst it's shown in xorg.conf together with my monitor's Horiz 33-81 and Vert 56-75 ranges.  

displayconfig-gtkdidn't didn't add much new except my Samsung 940mw wasn't listed. Surprisingly  it looked if my driver was nv on the first page and named as Nvidia GeForce FX generic.

Nvidia Settings Application shows it as 1.0-9755 but I'd also like to check this in the terminal but I've forgotten the command.

I tried altering the H and V ranges but no difference. What I didn't add the line
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
because I didn't understand all the figures, is this the direction I should proceed?

---

### Post by dougfractal on 2007-08-08
> I'm still missing the option for 1280 x1024 in Nvidia Settings and Screen Resolution in Preferences whilst it's shown in xorg.conf together with my monitor's Horiz 33-81 and Vert 56-75 ranges

I think in /var/log/Xog.0.log  it may say 1280 x1024 out of range.

[http://www.samsung.com/uk/products/monitors/lcd/lcdtvmonitors/ls19dowssedc.asp?page=Specifications](http://www.samsung.com/uk/products/monitors/lcd/lcdtvmonitors/ls19dowssedc.asp?page=Specifications)
from the spec it will only give max 1440x900.

Understand modeline [http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline)

from  [http://m.domaindlx.com/LinuxHelp/resources/modelines.htm](http://m.domaindlx.com/LinuxHelp/resources/modelines.htm)
# 1440x900 @ 60 Hz  (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
ModeLine "1440x900"  106.47  1440 1520 1672 1904 900  901  904  932  -hsync +vsync


[https://answers.launchpad.net/ubuntu/+question/4669](https://answers.launchpad.net/ubuntu/+question/4669)
> Section "Monitor"
  identifier "SyncMaster"
  vendorname "Samsung"
  modelname "SM940MW 1440x900 @ 60 Hz"
  HorizSync 31.5-88.0
  VertRefresh 50-90
  modeline "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  Option "DPMS"
EndSection


These values are a bit more conservative than the commented out ones above.

---

### Post by Handssolow on 2007-08-09
Thanks again for your help dougfractal.
The manual on Samsung's website for my SynMaster 940MW has the optimal resolution down as 1440 x 900 as you report. My Samsung "Quick Setup Guide" has the optimal screen resolution instead as 1280 x 1024 @60Hz.
Looking at the website the manual gives these figures-

Vesa 1280 x 1024 Horz 63.981 Vert 60.020 Pixel Clock MHz 108.00 Sync Polarity +/+
Vesa 1280 x 1024 Horz 79.976 Vert 75.025 Pixel Clock MHz 135.00 Sync Polarity +/+
Vesa 1440 x 900   Horz 55.936 Vert 59.887 Pixel Clock MHz 106.5   Sync Polarity -/+

So 1280 x 1024 seems to be supported.

I noticed in my /var/log/Xog.0.log that it was unable to load wfb module because it didn't exist. This probably isn't important with my GeForce 6600GT video card?? Also there was also this-

(II) NVIDIA(0): NVIDIA GPU GeForce 6600 GT at PCI:3:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 05.43.02.69.68
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 GT at PCI:3:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 155.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768


Next I inserting what looked like an an appropriate Modeline in xorg.conf for 1024 x 1024 which I cut and pasted but still no appearance of 1280 x 1024.

What does "No valid modes for 1280 x 1024" mean? A quick Google search and I start smelling a bug. So I changed over monitor lead from DVI to standard VGA lead, rebooted and had more resolution options than I knew what to do with -  even one at 1660 x 1024!!

Why do extra resolutions appear when I connect with a VGA lead than DVI?  Wouldn't VGA be slower than DVI?

---

### Post by dougfractal on 2007-08-09
> 
rebooted and had more resolution options than I knew what to do with - even one at 1660 x 1024!!
Why do extra resolutions appear when I connect with a VGA lead than DVI? Wouldn't VGA be slower than DVI?
I don't think it could validate them.


> Vesa 1280 x 1024 Horz 63.981 Vert 60.020 Pixel Clock MHz 108.00 Sync Polarity +/+
Vesa 1280 x 1024 Horz 79.976 Vert 75.025 Pixel Clock MHz 135.00 Sync Polarity +/+
Vesa 1440 x 900 Horz 55.936 Vert 59.887 Pixel Clock MHz 106.5 Sync Polarity -/+



```
# 1280x1024 @ 60Hz (VESA) hsync: 64.0kHz
ModeLine "1280x1024" 108.0   1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
# 1280x1024 @ 75Hz (VESA) hsync: 80.0kHz
ModeLine "1280x1024" 135.0   1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
# 1440x900 @ 60 Hz  (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
modeline "1440x900" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync

```
I think it was an error to have eg ModeLine "1440x900@60" .......

to use modeline you need to add to Section "device"
```
Option "UseEDID" "False"
```
or
```
Option "CustomEDID"
```
[B]
Usual WARNINGS apply
 AS ALWAYS, USE AT OWN RISK.[/B]

```
SubSection "Display"
Depth 24
Modes "1440x900" "1400x864" "1280x1024" "1220x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
```


I've all so been working on a new script called testx
[http://ubuntuforums.org/showpost.php?p=3157811&postcount=167](http://ubuntuforums.org/showpost.php?p=3157811&postcount=167)
create say a "xorg.conf.test" in /etc/X11/
and use testx it should make testing easier.

---

### Post by Handssolow on 2007-08-10
Thanks again dougfractal.
I had another play around with my xorg.conf with your new information but unfortunately I didn't make much progress. I restarted X and  was disappointed to see only 640 x 480 resolution available.

I'm back to 1024 x 768 @ 50Hz which is acceptable enough with my verifocal glasses.

---

### Post by dougfractal on 2007-08-10
It can get really hard to fine tune a system, sometimes it can just something so simple that its eairly missed.

without the modeline's did you ever get the "1440x900" "1400x864" "1220x768" "1152x864" and "1152x864" to work?

---

### Post by Handssolow on 2007-08-10
Thanks dougfractal, I can get always get the option of 1440 x 900, 1280 x 800, 1280 x 768 and many lower ones available in the "Nvidia Settings" Application, seemingly even when I didn't select it during configuration of xorg.conf, though1440 x900 isn't not my preferred resolution.

As mentioned before all this is using the DVI connection, using the VGA output  several more resolutions appear including the elusive 1280x 1024. Is this related to EDID?

---

### Post by dougfractal on 2007-08-10
> related to EDID EDID tell Xorg what the refresh rates are. So with VGA it looks if its left unconfiguerd, so it will/should take the modelines

Good luck to finding 1280 x 1024  just keep googling every now and then

---

### Post by mballow223 on 2007-09-29
I also have a Samsung SyncMaster 940mw I am trying Ubuntu for the first time.  Long time windows user.  I don't know how to set this up- i found the [Screen and Graphics Preferences] but when I click add model it asks for a driver file.... 

Just guessing that I copy and past the settings into some kinda file?

Thanks for any help.

---

### Post by mballow223 on 2007-09-29
I've been working on this... I downloaded and imported the inf driver file from the samsung website.  Then I set it on 1440x900 @ 65hz and at least i can see my entire screen, but it kinda shakes, like someone is jiggling the monitor back and forth.  Have no idea what to do next...

---

### Post by Handssolow on 2007-09-30
I've just spotted your postings mballow223,  have you made any further progress? Initially I bought our SyncMaster 949mw as a tv for use in the bedroom then moved it when I set up my Ubuntu PC. I suppose it's more of a wide screen tv but with DVI input for use as a PC monitor. After my previous experiments I was surprised that my system functioned differently if I used the DVI or VGA leads to connect to my Geforce 6600 GT AGP based video card.

I've got Applications>System Tools>Nvidia Settings which lists all my resolutions. I'm on 1024 x 768 which works well without any flickering but I have 1440 x 900 available if I wish.

I am using the Restricted Driver Manager's, Nvidia accelerated graphics driver but it's a bit of a bother whenever there's a kernel upgrade.

---

### Post by mballow223 on 2007-10-01
No, I have not made any more progress.  My video card is an ATI Rage 128 PRO, just an old cheapie.  Like I said though I'm a newbie.  My video just keeps shaking back and forth, it's really annoying.

---

### Post by Handssolow on 2007-10-02
Sorry to read you've made no progress. I satisfactorily used an Ati Rage Fury card previously before upgrading to my present Leadtec Geforce 6600GT card though I suspect I changed my video card before changing my monitor to the Samsung SyncMaster 940mw.
Are you setting the correct ranges in Xorg?
sudo dpkg-reconfigure xserver-xorg
Mine are Horiz 33-81 and Vert 56-75 with my current resolution choice of 1024 x 768 at 50 Hz refresh showing in System>Preferences>Screen Resolution.

Can you select other resolutions and what are the effects?

A side issue with running an Ubuntu system is that we might frequently use older hardware. Rather than having bought a PC  with a pre-installed OS from Bill G's company, we explore the alternatives and frequently we use older hardware.

So what item in your hardware is the weakest link still seems illusive to identify but obviously this also depends on what applications we want to run. I have been surprised how my various hardware upgrades haven't produced the improvements in performance that I was expecting. Perhaps in my case when Skype finally produces a video web-cam version for Linux I will find out.

---

### Post by dougfractal on 2007-10-02
> **mballow223 said:**
> No, I have not made any more progress.  My video card is an ATI Rage 128 PRO, just an old cheapie.  Like I said though I'm a newbie.  My video just keeps shaking back and forth, it's really annoying.

reduce your default depth 16

> **az said:**
> The ATI rage 128 is supported by the native ATI driver.  If it only has a small amount of ram, you may need to reconfigure X to use less of it so that DRI (hardware acceleration) is enabled.  You may need to lower your resolution or color depth.

By default, Ubuntu uses the maximum resolution and color depth.  Even if you switch down to a lower resolution, the ram is not freed.

You need to boot into recovery mode and run

dpkg-reconfigure xserver-xorg

and try using 1024x768 at 16-bit for a card with 16 megs of ram, for example.  If your card has less ram, you need to go even lower.

---

### Post by mballow223 on 2007-10-02
I cant boot into rescue mode because this version of ubuntu installed from a live cd.                 Get this though, I did manage to get the monitors settings right by importing the inf file for it.  My screen is pretty stable, but its moves when i'm typing..... not alot, just enough to aggrivate me.....  so back to my XP machine for now, I'll try again tomorrow.

---

