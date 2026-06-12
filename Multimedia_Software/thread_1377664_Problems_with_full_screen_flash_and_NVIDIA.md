---
title: "Problems with full screen flash and NVIDIA"
date: 2010-01-10
forum: Multimedia Software
---

### Post by SNR99 on 2010-01-10
I am realtive newbie to Linux and have Unbuntu 9.10 with all the updates applied.  Ill start with my first problem...

I have downloaded the recommended NVIDIA driver for my Quadro FX 1400 graphics card which has 256 MB RAM.  I have my laptop in a docking station and from the docking station is a DVI to HDMI converter then HDMI cable to my TV (the idea is to use it as an internet TV slave! :popcorn:).  When I come to configuring the NVIDIA X Server, it correctly detects both my laptop screen and my TV via the HDMI connection.  However, when I come to save the settings for the X server and go to restart it, it cannot save the configuration file.  This is most annoying as it does not allow me to use the dualview I need.

The second problem comes when I use something like the BBC iplayer or anything that uses the flash player.  I have the latest flash player with Firefox which works fine in non-full screen mode.  However, when switching to full screen, the CPU load jumps to 100% and the playback is really jerky.

Had this running the beloved windows XP before and could handle full screen no problems.  I have seen a few posts here which show workarounds to zoom in on the small screen on Firefox but would prefer to run it in the full screen mode.

Can anyone help with my dilemmas?!:D

---

### Post by Jenkins1 on 2010-01-10
To so that you save the display configuration you need to open the terminal (found Applications > Accessories > Terminal)
and type 
sudo nvidia-settings
make all of your changes then click "save changes to xorg" then it should keep the settings.

---

### Post by SNR99 on 2010-01-10
Thanks for your quick reply.  I have tried this and unfortunately, it will not allow me to save the xorg file.  It just says it cannot access it.

---

