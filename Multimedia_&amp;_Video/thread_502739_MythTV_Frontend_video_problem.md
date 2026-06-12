---
title: "MythTV Frontend video problem"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by mx-5 on 2007-07-17
I've got a couple of identical old PCs - Compaq iPAQ P733 Legacy Free PCs.  Intel 810 chipset, integrated video, sound, nic, etc.  On paper, nice machine as a front end.

I put more ram in one (256MB) and went ahead with a Frontend and Regular Desktop install according to this doc using Feisty Desktop i386 CD.
[https://help.ubuntu.com/community/MythTV_Feisty_Frontend_Desktop]("https://help.ubuntu.com/community/MythTV_Feisty_Frontend_Desktop")
Connected to my MythTV Backend which has a Hauppauge PVR250 card.  Even had video at 1280 x 768 displaying in MythTV and had no problems with video.

I put less ram in another (128MB) and did a Frontend Only install according to this doc using Feisty Alternate i386 CD.
[https://help.ubuntu.com/community/MythTV_Feisty_Frontend]("https://help.ubuntu.com/community/MythTV_Feisty_Frontend")
Selected 640x480 only since this wasn't going to be a desktop and didn't need the high resolution.  Connected to the same MythTV Backend.  Audio sounded fine, but video was dropping frames and was very jerky.

Test 1:
Improbable, but simple test.  I changed the box with 256MB to run at 640x480 just to make sure there's nothing funny about that resolution.  No problems, still smooth.

Test 2:
I upped the RAM on the 128MB box to 256MB.  Still jerky.

Test 3:
I noticed the full desktop had the kernel upgraded from 2.6.20-15 to 2.6.20-16 from Synaptic, but the desktop-less machine skipped this upgrade from the apt-get, so I did apt-get dist-upgrade.  With the desktop-less machine at 2.6.20-16, TV was still jerky.

Maybe this will lead to something:  The one thing I noticed is that the text with the Desktop machine looked as expected (same as any other Ubuntu desktops), while the desktop-less machine had significantly smaller text which are slightly blurry.  What I am referring to are the text that says "Pre-scaling themes", or if I typed in a username/password, or in MythTV, if I go into Information Center/System Status.  (The MythTV menus look fine, btw.)

Before I do a reinstall of the 128MB desktop-less machine with Alternate CD again, except to select the higher res during install, does anyone have any suggestions?  Any ideas whether there are differences between the Desktop install and Alternate install which will cause such problem, and whether there's a patch I can apply to the Alternate install to resolve this issue?

Thank you!!

---

