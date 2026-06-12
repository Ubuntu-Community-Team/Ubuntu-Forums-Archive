---
title: "[SOLVED] Problems with PVR-350"
date: 2008-04-03
forum: Mythbuntu
---

### Post by tvdm on 2008-04-03
Hello all,

I had original posted this in 'Absolute Beginner Talk', because that is what I am, however, I get a lot of lookers but no replies. I am hoping someone here could help.

I have a Hauppauge PVR-350 and I am trying to use it with Mythbuntu 7.1. I am following the content at the link:
[https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Gutsy_hardware_pvr-350_TV-out)

to try to get a video to play on my TV via the TVOut from the card but when I get to the point

cat Silhouet2001.mpg > /dev/video16

I get sound and little bit of the picture on my TV but I mostly have a large black square centered on the display with the video playing in the background; I can see some of it around the edges. The test image (i.e. vertical lines of colour) appears fine. I decided to move on to the X11 configuration to see if part of this had any effect and have completed the entire HOW-TO but there is no change in the display.

Could the X11 configuration be causing my problem or would it be the ivtv driver? Should I be concentrating on xorg.conf?

Anybody have any suggestions or maybe some additional tests I can do on the card to make sure it is working?

Thank you
tvdm

---

### Post by tvdm on 2008-04-03
I ended up reinstalling Mythbuntu with the card installed this time while installing Mythbuntu in the hopes that it would detect the card and configure it appropriately. That either fixed the problem or the fact the I left the default V4L setting for tuner card instead of selecting the PVR-x50 setting. Either way, it is working now and I am not willing to mess with it.

---

