---
title: "Fix ATI Radeon driver issue"
date: 2012-01-04
forum: Multimedia Software
---

### Post by GuilhermeBrant on 2012-01-04
Hi,

I've been using Ubuntu 11.10 with the built-in open source drivers for my Ati Radeon Xpress200, but I noticed some problems (not rendering properly, freezing) with specific video types (like some .mp4, .mpeg , etc) , so I decided to try the proprietary version for it (catalyst). But after the installation failed, I figured out that ATI does not support my driver anymore for 11.10. As I'm not that wise linux user, I guess I messed things a little, and now, when I try to log in, it starts loading, suddenly stops and come back to the login display again. I can still use the command line to try to fix it. I tried removing fglrx, and reinstalling xserver-xorg-video-radeon, but didn't make any difference.

Can someone help me figure it out?

Thank you very much,
Luiz.

---

### Post by QIII on 2012-01-04
What commands did you issue to remove the proprietary driver?

Edit:

In case I don't get back around to this, please check these two:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

and

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

Unfortunately, you won't be able to use your browser to look at those while you are working, so either have a laptop handy or print them out.

Before you do anything, please read carefully and ask for help if you don't understand something BEFORE you get tangled up more.  Ask what you need to first.

---

### Post by GuilhermeBrant on 2012-01-05
Hi QIII,

Thank you very much for your help. I managed to remove both fglrx and -ati and reinstalling the latter from your instructions and now everything got back to normal.

---

