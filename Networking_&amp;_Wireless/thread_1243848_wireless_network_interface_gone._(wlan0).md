---
title: "wireless network interface gone. (wlan0)"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by ladi on 2009-08-18
hi! 

i was trying to patch my ath9k drivers with the madwifi drivers.

after following the steps on : [http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)
and i reboot. my wireless device failed to work.

when i type iwconfig, i get 
@lado:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

hso0      no wireless extensions.

normally i would get **wlan0** included with the *80211 comments*.

also i could see AP or wireless networks when i boot my pc. but now i can't see any networks anymore.

my pc is fujitsu siemens pa 3553, amd atheron, 4G RAM

Also after so many troubleshooting i always get this warning: 
[B]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
[/B]
PLEASE HELP ME.

---

### Post by colomob on 2009-08-18
I have the same problem, but, i have an Hp Pavillion.. =/
Every time that i run in terminal the sudo lshw -C network command it appears that the network is disabled. The switch to turn on the wireless network is ON, but, the light shows it as OFF.

---

