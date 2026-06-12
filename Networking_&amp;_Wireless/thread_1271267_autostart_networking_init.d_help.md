---
title: "autostart networking init.d help"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by xshad0wfx on 2009-09-20
Hi im trying to get my wireless usb (wlan0) to autostart on init.d when the machine is turned on.  This is so i can use wake on lan to tun on my media server and then fuppes and my wifi can auto connect and start without logging into the machine.  pretty nifty eh? but the problem right now is i cant manage to get the wlan0 to auto start. after searching on google i managed to find nothing useful for it to auto start in init.d but only after logging in.  If someone knows how to get the eth0 to autostart in init.d without logging in thats ok too.

---

### Post by Iowan on 2009-09-20
I seem to remember a thread suggesting interfaces defined in */etc/network/interfaces* start on power-up - whereas those defined by Network Manager don't start until login.

---

### Post by slakkie on 2009-09-20
Hi,

I'm busy writing this guide: [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic)

The part you want is already done. Automatic configuration for laptops is unfinished, but you should be able to set it up for one location. Provided your network card is supported by wpa_supplicant.

Best of luck!

---

### Post by xshad0wfx on 2009-09-21
sweet! thanks!

---

