---
title: "Automatic modprobe?"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by giburrito on 2010-11-11
I recently purchased a Belkin Basic (N150, but linux is reporting it as full 300 =D) usb dongle. I have managed to get it all working except for the pesky fact that I have to manually run modprob r8192s_usb in order to get ifconfig and iwconfig to show my wlan0.

I found another thread that walked through putting some extra stuffs into the drivers and rules files so that the id's for this dongle will be picked up by the r8192s_usb driver.

Everyone else was able to just reboot and the system would automatically load the driver. In my case I always have to manually run modprobe r8192s_usb and then down and up the wlan0 interface in order to use the wifi.

Is there anyway to have it automatically ensure that the driver gets loaded?

FYI: I'm running Karmic that comes as the basis for XBMC Live.

As an aside, is there anyway to trick software that is looking for eth0 to instead look at the stats for wlan0?

Thanks!

---

### Post by uncaspi on 2010-11-11
Put the modulename in /etc/modules
then it`s loding at boot. The other question you could bring your card down at boot up. If you don`t want eth0 up type 

/sbin/ifconfig eth0 down

in /etc/rc.local

---

### Post by giburrito on 2010-11-11
Fantastic, just what I needed.

All of a sudden XBMC started recognizing my wlan ip and such without doing anything else.

Thank you much.

---

