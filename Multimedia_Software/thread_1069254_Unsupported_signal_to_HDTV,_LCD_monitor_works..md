---
title: "Unsupported signal to HDTV, LCD monitor works."
date: 2009-02-13
forum: Multimedia Software
---

### Post by langerak on 2009-02-13
I have a strange issue and i have seen it addressed many times, altho in a different manner.

I have a Point of View GeForce 9400GT graphics card and as for the 3D support it works.
I have a Samsung SyncMaster 913N hooked to the VGA bus of the card and a Philips 37PFL5603 HDTV connected to the DVI bus. It is connected DVI - HDMI.

I installed the latest nVidia driver and managed to setup the monitor settings for both the screens. My Samsung now runs at 1280x1024, but my HDTV keeps saying "Unsupported video format", whatever resolution / frequency i choose, it stays that way. The strangest part is is that it shows BIOS POST screens and the Ubuntu startup logo, but as soon as it is starting X, it fails. I also tried the standard X Vesa driver and that one works with no problems, only no 3D support etc.

Just to mention, it is a full HD TV, so it supports 1920x1080 res. Got it earlier working on a couple of desktops and notebooks.

Now my question is, how to fix this, i saw alot of suggestions like "enable vSync", "change the EDID information (which my TV reports correct)", "use nvtv out". None of these tips works...

One last point which i find strange: Last week, my old 8400GS card from XFX died, but had always worked with Ubuntu / MythTV without any problems on the same TV, now i replaced it with the current 9400GT and all these problems rised. I even did a couple of reinstalls of Ubuntu, without succes...

I really hope someone has a proper solution as i want to use this box for MythTV for playing my HD content :).

Any help is appreciated and thanks in advance!

UPDATE:

When i launch the screensaver panel and test some screensavers (not all work), the screen of my TV starts flickering and sometimes i see the ubuntu background showing up in the top left corner of the screen.
Now i am terribly confused lol :P

---

### Post by langerak on 2009-02-14
Little bump:

Tested my HDTV on my Dell Inspiron 9400, which has a GF7900GS card.

Installed Ubuntu and with one click in the nvidia control panel, i got the panel working flawless!!
In the infomenu it says that it is connected via Single Link DVI and on my desktop it says Dual Link DVI, could that be a problem? The EDID info is on both machines the same, so it is reporting correctly.

Now i am stuck, not knowing what to do... :P

---

### Post by langerak on 2009-02-14
Just updated the firmware of my TV, but that didn't seem to fix the problem :(.

Tried beta drivers, old legacy drivers, nothing works...

I am getting the terrible feeling that it is a problem with the card as i tried an other Point of View card (GF8400GT) and has the same problem...

Still no-one has a solution or hint??

---

### Post by CRIMPS on 2009-04-16
I, too, have a Philips HDTV.  I have tried to get tv-out working via HDMI, but I receive the "Unsupported Video Format" message as well.  I need to test this a little further as I have always blamed the lemon that is my Philips HDTV.  :(

Im subscribing just to keep my eyes on what you find.  Good luck.

---

### Post by dtmonterrey on 2009-10-01
Hi

I have a NVIDIA 9400 GT with VGA, DVI and HDMI

I connected an LG W2042S to the VGA connector and a Philips 37PFL5603D to the HDMI connector.

I got image on the LG and on the Philips but from time to time (20secs~1min) my Philips HDTV becomes black for about 5 seconds. Previously I had a NVIDIA 5800 and a NVIDIA 6600 with the Philips connected  to the DVI connector using an adapter DVI<->HDMI and everything worked fine.

I'm looking for a solution, but probably I will buy a new card (I'll try a 9600 first)

---

### Post by dtmonterrey on 2009-11-10
Hi again

I didn't get a 9600 card, but installed a 8400 and it's working really well now. Cans thi be a problem with DRM over HDMI? This card doesn't have a HDMI, just D-SUB, TV-out and DVI (I didn't had done any benchmark, but this card is performing +/- like the 9400 but it's cooler).

I also asked my country support for Philips but they only replied saying I needed to update my computer drivers... :mad:

---

### Post by CRIMPS on 2009-12-16
Thanks DTMonterrey.  There is some interesting information there.  I think I will take this up again as I am running the 195 NVidia driver installed and I am motivated to troubleshoot this again.

---

### Post by dtmonterrey on 2010-03-24
Hi folks... it's been a while since I last reported and I have bad news: using the 8400 it seems to work ok, but when it started to heat up "the black screen" came on again :(

Then I though it could be a heat problem (both boards are fanless) so I put the 9400 again and added 2x12cm case fans.

This seamed to resolved th problem... not the case! Even with the board not surpassing 50ºC I got some "black screens" (one in about 3~5min) and only during video playback (on the TV or the main monitor).

Now I'm updating my TV firmware to the latest one (ver. 000.064.079.000) but according to the change log it will only add an option to the main menu :(

So, no big hope for now...

---

### Post by dtmonterrey on 2010-09-17
It's been a while since I reported last time. Meanwhile I got the problem somewhat solved out by using the open source driver. I tried with the more recent 256.53 version of the proprietary driver, but the issue is still there. The only setback is that I don't have 3D... :(

I upgraded to Maverick and I going to try the experimental 3D support on nouveau...

---

