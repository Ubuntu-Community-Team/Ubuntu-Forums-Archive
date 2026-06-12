---
title: "Wireless Stopping, this works 4 me so far"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by rasturn on 2010-05-05
lease detach the wire. Next, please do:
Code:
sudo gedit /etc/NetworkManager/nm-system-settings.conf
If managed = false, please change it to true. Reboot.
 
Now is it working?
__________________
Registered Linux User #374501
Fabricati diem, pvnc
Anyone else want to try make sure its not a placebo
it stopped again lasted longer

---

### Post by rasturn on 2010-05-07
my wireless would work about 30 min before it would drop out after some reading i disabled "N" on the router. and so far i've gone hours without a drop.
10.04-intel 5100 wireless.

---

### Post by Iowan on 2010-05-10
Merged threads

---

### Post by slouse on 2010-05-12
That's great, managed=true has solved my problem, thanks a lot! Last time, I solved it by re-installing wpa-supplicant as recommended in [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/575128](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/575128), but this time, it didn't help. "Wirless diconnected" was greyed out and wasn't to be changed until I changed the setting in nm-system-settings.conf.

---

### Post by emmiesix on 2010-05-14
seems to be working for me, I was dropping after maybe 1 page load at best, and it was getting worse??  So thanks!

---

