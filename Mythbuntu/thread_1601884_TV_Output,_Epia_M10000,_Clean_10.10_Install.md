---
title: "TV Output, Epia M10000, Clean 10.10 Install"
date: 2010-10-20
forum: Mythbuntu
---

### Post by raHumphrey on 2010-10-20
I've just tried a clean install of Mythbuntu 10.10 on Epia M10000.  Everything seemed to be going as I expected, until I tried to enable the S-Video TV output.  I know the TV out works as I achieved this in 9.10, but can't get it working this time.

Attached are a number of Xorg.0.log outputs, under different scenarios.  I've also included one dmesg output, should that provide any useful information.

First Xorg.0.log is for when the BIOS is set to CRT only and my (old) TFT is attached and no S-Video cable is connected.  This works without problems or the need for any xorg.conf.

Second Xorg.0.log is for when the BIOS is set to TV only (PAL), no CRT attached and the S-Video connected to the TV.  The log indicates that the S-Video cable is detected, but it tries to use NTSC.  I don't see anything on the TV in X, although can see it booting and switching to the console works, although switching back I am again presented with a black screen.

To get the output standard to PAL, I tried using the xorg.conf from my 9.10 installation.  This improved the situation to the point that something is now displayed on the TV.  However, it's definitely not right! The width of the desktop fills the width of the TV (give or take some overscan) but the whole TV screen height is used for only half the desktop height, alternating between displaying the top half and the bottom half of the desktop.  I suspect this might be because it is displaying the top half in one field and the bottom half in the other, although cannot confirm this yet.  There also seems to be a sync issue because everything displayed oscillates up and down on the screen by about a cursor-height.  I again suspect this moves every frame, but cannot confirm this.

If someone could check my xorg.conf or suggest anything I should try then I'd be very grateful.

Thanks :-)

---

