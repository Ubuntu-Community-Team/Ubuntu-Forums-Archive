---
title: "Bar of Video Gunk with Intel Integrated Video"
date: 2009-04-28
forum: Multimedia Software
---

### Post by AtlantaBob on 2009-04-28
Hi all. I've got an old Dell SC420 (Celeron) with Intel Integrated Graphics and 2 GB of RAM. I'm running Ubuntu 8.10 on it, and it's hooked up to a large Dell flat screen 2407WFP. It's connected using a standard VGA cable. About two inches from the bottom of the screen, there's a quarter-inch band of "graphics gunk" -- just where the display is distorted and pixelated. 

Right now, in GNOME and XCFE (my main environment), it stays steady as long as there's no window moving over it. Once I drag a window across it, however, the window becomes distorted where the window passed over the band - lots of artifacts and such. Window Composting in XCFE is turned off. If I'm running Open Office Spreadsheet and it's maximised and I scroll through the sheet, the artifacts corrupt the entire display. For what it's worth, there's no distortion of the mouse pointer when it moves over the bad area -- which makes me think this is some sort of window composting-type of error?

Any suggestions as to what I do to get rid of this? It's awfully annoying... Just to reiterate, the same thing and same symptoms happen in GNOME.

Thanks in advance.

---

### Post by AtlantaBob on 2009-04-29
This may be a very dumb question, but are there proprietary drivers for Intel onboard video? If so, could someone point me in the right direction (some google searches have hinted that they might exist, but I haven't been able to find any.) I've checked the System/Hardware Drivers and it confirms that no restricted drivers are being used -- and doesn't show any available.

---

### Post by VMC on 2009-04-29
Post out output of the command below so we know what Inel chip you have.

```
lspci -nn|grep VGA
```

---

### Post by Arup on 2009-04-29
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

If you do have Intel chip, this is for you, latest stable Intel and other drivers from the Ubuntu X team.

---

### Post by AtlantaBob on 2009-04-29
Thanks, output of the driver command is here:

00:02.0 VGA compatible controller [0300]: Intel Corporation E7221 Integrated Graphics Controller [8086:258a] (rev 04)

Arup, I'll try to look at that link. Thanks. Any thought as to whether I should have any concerns if I'm still running 8.10?

---

### Post by AtlantaBob on 2009-04-29
Well, I installed the new drivers. If anything, it appears that it moved the line of gunk *up* on the monitor about an inch..... Any other ideas?

Thanks.

---

### Post by AtlantaBob on 2009-04-30
FYI and for other people's knowledge, upgrading to 9.04 did the trick. No more graphics gunk!

---

