---
title: "ubuntu detects 32&quot; TV instead of 42&quot;"
date: 2009-09-18
forum: Multimedia Software
---

### Post by anystupidname1 on 2009-09-18
Both Jaunty and Karmic detect my Panasonic **42"** HDTV as a 32". The resolution of 1920x1080 is picked correctly but about a half inch of the outside perimeter of the screen is displayed outside the display area of the TV. I suspect this is because of a scalling / pixel thing? Since Ubuntu thinks the TV is only 32" instead of 42"? Does anybody know how to get the right "scaling"? Besides changing to a crappier resolution which doesn't use the entire HDTV screen area, I don't know what to do. xrandr options don't seem to offer parameters for this? Any assistance would be much appreciated!

---

### Post by LowSky on 2009-09-18
what option are you using to get the image on the tv?
DVI, HDMI, VGA?

does your TV have a setting option for adjusting the screen, I know mine does when its in VGA (RGB as my TV calls it) mode.

---

### Post by anystupidname1 on 2009-09-18
DVI to HDMI via a "ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]" (card has a DVI and a VGA head) (using VGA will only pass a crappier signal)
Sorry, thats obviously important.
TV is a TH-42PZ80U

---

### Post by adenewton on 2010-11-05
Just bought a panasonic 42" and have the exact same problem as above, don't suppose anyone can help?

---

### Post by wkulecz on 2010-11-05
Try using the VGA cable.  I run 1920x1200 LCD monitors over the VGA and the signal is in no way "crappy" and it is scaled and centered correctly.  My monitor (Sony) has never been picked up correctly over DVI, since 6.06.

In fact on Windows I run dual 1920x1200 displays, one VGA the other DVI and you can not tell the difference.  The VGA cable is more flexible, longer, easier to route and way less expensive.  Count me as a total non-fan of DVI, whcih appears to be a total rip-off, at least below 1920x1200 resolutions.

---

### Post by tgm4883 on 2010-11-05
I've never heard of a system detecting the size of display (yes the resolution, but not size). It does get EDID information from the TV and that may be getting something set incorrectly.

Sounds more like you have an overscan issue. There is likely a setting in the proprietary control panel for your graphics card (nvidia settings or catalyst)

---

### Post by anystupidname1 on 2010-12-15
I can confirm that as of Maverick, it detects this TV properly.

---

