---
title: "Nvidia ION Tiny text"
date: 2012-09-06
forum: Multimedia Software
---

### Post by slippyjim on 2012-09-06
Hiya,

Ive got an Acer Revo R3610, 2GB RAM, 320GB and I am having all sorts of problems gettign the text on the desktop to be the correct size - after googling it appears to be a DPI setting.
I have tried lubuntu 10, 11.10 64bit & 12.04 64bit
It has the nvidia drivers v295  that installs from Additional Drivers,  Ive also tried v304 from nvidia website with the same results
   hdmi into sony 40" lcd

I have tried manually editing xorg.conf file with the following

Section "Monitor"
    Option         "UseEdidDpi" "False"
    Option         "DPI" "55 x 55"
EndSection

But when I reboot, lubuntu never starts back up again, what am I doing wrong???
I calculated my DPI from pxcalc.com 

Usually my xorg.conf file only has one section in it and I think with v10 there wasnt even an xorg.conf file at all, is this normal?

The only time it has work properly on my TV was with Ubuntu 12.04 but then video in XBMC was really juddery 

TIA

---

### Post by marinara on 2012-09-06
did the normal way of changing text size not work for you? [https://help.ubuntu.com/community/Lubuntu/Setup](https://help.ubuntu.com/community/Lubuntu/Setup)
if that works you can delete, the .xorg.conf you don't need it in ubuntu

---

### Post by VinDSL on 2012-09-06
> **slippyjim said:**
> Section "Monitor"
    Option         "UseEdidDpi" "False"
    Option         "DPI" "**[COLOR="DarkRed"]55 x 55[/COLOR]**"
EndSection
Whoa!

I run 96x96 on LXDE machines...  :)

Here's the monitor section from my xorg.conf:

```
Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL 1907FP"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
    Option         "DPI" "**[COLOR="DarkRed"]96 x 96[/COLOR]**"
```

Might want to try that.

---

### Post by slippyjim on 2012-09-07
In Lubuntu 12 I managed to change the text, but it doesnt change the text size in the terminal window or on the task bar. I can live with the taskbar but the terminal would just be a pain.....

I got that DPI figure from the website, remember its on a 40" TV so the DPI will be a lot lower than a monitor. Even if I specifiy the wrong DPI the desktop should still load right?

Also from what Ive read if you specify DPI you have to do the Option         "UseEdidDpi" "False" line as well

---

### Post by marinara on 2012-09-07
xterm or lxterminal?

---

### Post by slippyjim on 2012-09-07
LXterminal
I just found it, simple....... Edit -> Preferences and the font size is right there

I managed to alter the icon size on the taskbar but not the actual font size, strange but I can live with that

---

### Post by gordintoronto on 2012-09-07
To use XBMC in 12.04, you might want to Google: vdpau xbmc

From what I have read, the "juddery" is a setup issue.

This page might help:
[http://wiki.xbmc.org/index.php?title=How-to:Fix_common_1080p_playback_issues](http://wiki.xbmc.org/index.php?title=How-to:Fix_common_1080p_playback_issues)

---

