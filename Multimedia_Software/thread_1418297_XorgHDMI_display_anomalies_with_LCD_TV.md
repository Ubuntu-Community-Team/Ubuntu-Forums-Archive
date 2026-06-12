---
title: "Xorg/HDMI display anomalies with LCD TV"
date: 2010-02-28
forum: Multimedia Software
---

### Post by woedend on 2010-02-28
Hey guys...haven't posted here in a while.  Please let me know where the best place to post this is or which package with which to file a bug report.
I just bought a new desktop with integrated intel graphics and built in HDMI.  I don't have a monitor, only a 42 inch LCD TV.  Now, when I plugged in the HDMI cable, when ubuntu loaded, it was oversized(overscanned) cutting off both panels(think zoomed in a bit).  After failing to fix, I bought an ATI HD4350.  When using the open source ati drivers(default on reboot), the screen looked perfect and fit perfectly when using the DVI to HDMI cable to the TV, was a bit UNDERsized when using a regular HDMI cable to the HDMI port on the new video card.  Now, when I installed Catalyst...same problem as before.  Entire image was overscanned using either port.  Decided to get a better video card anyways, so returned ATI for Nvidia 9500.  When booting again into a clean install, with nv drivers and using DVI-> HDMI cable(9500 doesn't have HDMI out), the image again fit perfectly on the TV.  When installing the Nvidia proprietary driver, image goes back to being overscanned(Exactly same proportion as intel HDMI out and ATI with catalyst).  Thankfully Nvidia gives an overscan correction tool that I scaled the picture down with, but it's ever so slightly off center or our of proportion(that is, it leaves small black strip on either side when height is adjusted perfectly).

In a nutshell, the open source drivers display perfectly.  Proprietary and intel drivers are overscanned.  

Now, to confuse you anymore, with Lucid, even the open source ATI driver is overscanned by default.  I'm trying to track this problem down and have no idea where to start.

Thanks for reading.

---

### Post by gspat on 2010-02-28
Hi!

Same thing here... but I'm not sure it's a driver issue. 

Your overscanning can be helped somewhat by going into your tv's menus and having it autotune to the signal. that worked better for me than than playing too much with the nvidia controls.
Do you also have the issue where hdmi just doesn't look "as good" as your other display options? kinda like it's falling back to thousands of colors instead of millions, so you get a kinda grainy look to the image?

The reason I'm leaning towards it not being a driver issue, is that it looks exactly the same in windows 7 (dual boot) with the same driver version. 

I kinda put hdmi on the backburner for now, since the other options work really well for me.

---

### Post by woedend on 2010-02-28
The picture definetely lacks in overall sharpness!  The only reason to make me think it's a driver issue is that nv and ati work as expected, catalyst and nvidia and intel are borked.  This could be related to 3d acceleration itself, maybe KMS?  I don't know.  

With windows at least, I never actually logged in but did boot into it a couple times to see the setup screen, and it was at least scaled properly.

As for the TV, its a nice TV, but has no such tune to signal/autocorrect feature unfortunately.

---

