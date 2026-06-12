---
title: "No HDMI video output nor HDMI audio output - Ubuntu 10.10"
date: 2011-04-13
forum: Multimedia Software
---

### Post by Pikkolo on 2011-04-13
Hello there and thanks for attention,

I have a Gainward GTX 460 SE and an LG 32 inches lcd tv.

On Windows, both HDMI video and HDMI audio work beautiful.

But if I boot Ubuntu 10.10, even if the HDMI cable is correctly connected, the LG tv doesn't receive any HDMI signal from the pc. The Sound panel of Ubuntu shows something that I guess regards HDMI audio, but nothing comes out of the tv speakers. Of course I already installed the restricted drivers that are automatically suggested by Ubuntu when I go to Administration - Additional Drivers.
I must say that the VGA connection works perfectly allowing 1920 x 1080 resolution. But I want to use HDMI video and audio with my beloved Ubuntu ehe

May I please ask for your help ?

Peace and Love

Marco

---

### Post by BicyclerBoy on 2011-04-14
I would suggest the default ubuntu driver you have selected is a bit old for your hardware.

Could try a more up-to-date driver, in easy package form, from couple of ppas..
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
This will get you nvidia 270.14

Getting the HDMI audio working can require more effort but you need the get video working first.

To help debug the HDMI video connection, reconnect monitor by HDMI & reboot
If you have no GUI hit <CTRL> <ALT <F2> & console login, copy the below log file to a backup file.
 ...post your log file:
/var/log/Xorg.0.log

---

