---
title: "Wireless Stopped Working on Kernel Update"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by SneakPeak on 2012-10-21
Hi,

I am running ubuntu 10.04.  On a kernel update from 2.6.32-41 to 2.6.32-42 the wireless stopped working.

Any ideas on how I can fix this?

Thank you

Adrian

---

### Post by varunendra on 2012-10-21
If not a problem, switch to 12.04 LTS to enjoy superior kernel and better packages. 64 bit if your systems supports that. A clean installation is always recommended, but if you prefer to upgrade, make sure to backup your system (by imaging the system partition(s) using clonezilla or any software of your choice) so you can revert to current state in case upgrade fails or something else goes wrong. Backup your data anyway.

If, however, you prefer to stay with 10.04, please run the following command to download and run a script (courtesy dave, wildman & others) that will create a summary of your wireless settings (just copy-paste the command in a terminal):
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will create a file named "netinfo.txt" in your home directory. Copy-paste its contents here.

---

