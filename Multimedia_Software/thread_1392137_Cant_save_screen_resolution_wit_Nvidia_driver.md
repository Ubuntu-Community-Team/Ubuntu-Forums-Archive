---
title: "Cant save screen resolution wit Nvidia driver"
date: 2010-01-27
forum: Multimedia Software
---

### Post by ThaddeusW on 2010-01-27
Hello,
Since I upgraded to 9.04 a while back I have had this annoying screen resolution issue. Every time I log into my Ubuntu system the screen resolution defaults to 1280x1024. My preferred desktop resolution is normally set at 1680x1050. So each time I log in I have to open the Nvidia control panel and manually set the screen resolution to 1680x1050. Even after logging out it will still go right back to 1280x1024 when I log back in.

But the funny this is I am almost positive the login screen resolution is 1680x1050 because the picture is crisp unlike the blurry and distorted picture at 1028x1024. I have tried everything from manually editing the x.org conf file to running the Nvidia control panel as root. Nothing saves my preferred resolution of 1680x1050.

My Nvidia driver is version 190.42 and Ubuntu version is 9.04. The monitor is an ASUS VW192T+ which is detected by the Nvidia driver.

Any ideas on how to fix this? 
Thanks

---

### Post by ThaddeusW on 2010-01-29
Anybody?

I know this is/was an issue because I once found a similar thread but it had no cure listed.

---

### Post by ebharv on 2010-01-29
Try this [post]("http://ubuntuforums.org/showthread.php?p=8389348#post8389348"). If that doesn't work try the second part of this [post]("http://ubuntuforums.org/showthread.php?p=8744315#post8744315").[ ]("http://ubuntuforums.org/showthread.php?p=8744315#post8744315")

---

### Post by Andrew_P on 2012-02-17
> **ThaddeusW said:**
> Hello,
Since I upgraded to 9.04 a while back I have had this annoying screen resolution issue. Every time I log into my Ubuntu system the screen resolution defaults to 1280x1024.

Are you using a KVM (keyboard-video-mouse) switch with your setup?  I skipped Ubuntu 9.x, but noticed this effect the first time with Ubuntu 10.04 when I inserted my Belkin OmniView SE 4-port KVM switch between the keyboard, monitor and mouse.  On startup the computer is trying to query the hardware to find out what's plugged in and the KVM switch is apparently not sending the SDA and SDC data signals (VGA pins 11, 12, 15) through to the computer's video card, so it defaults to a setting it thinks *may* work with the monitor, based on configuration information it had the last time the system ran.  The solution is to hard-code the resolution for the boot screen and the GNOME desktop, overriding any attempt of plug-and-play automatic configuration.

I have this very same problem with my Windows 98 machine that shares the same peripherals:  I select the monitor driver, but the next time the system starts, it reverts to a generic 640x480 16-color driver.  The solution in Windows is to tell the system in the Advanced Settings panel to not automatically detect Plug-and-Play monitors.

If you have a KVM switch, it may be helpful to remove it and plug the monitor, keyboard and mouse directly into your Linux box while you're getting it set up.  Once you have determined the Plug-and-Play setup configuration, note it and hard-code it into the various configuration files.

---

