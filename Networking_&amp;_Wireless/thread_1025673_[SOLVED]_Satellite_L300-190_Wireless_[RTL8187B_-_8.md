---
title: "[SOLVED] Satellite L300-190 Wireless [RTL8187B - 8198chip]"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by mali2 on 2008-12-30
Toshiba Satellite L300-190 Wireless
Realtek RTL8187B Wireless 802.11b/g 54Mbps USB 2.0 Network Adapter


1. by using the lsusb i got the following information about my wireless:
"Bus 008 Device 002: ID 0bda:8198 Realtek Semiconductor Corp"

2. Then according to the reference of ubuntu forum i used the steps for manually configuring my wireless 
[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b) and then to be more specified about my wirless i used the reference below.
[http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi-old.html](http://www.doc.ic.ac.uk/~pgp/personal/logs/r8198-wifi-old.html)

3. after doing all the steps according to the guide... I used:
       
          ....Step 4. patch -p1 < 2.6.24.patch
              Step 5. Make changes in the /wifi/rtl8187/r8187_core.c (Search for 2 lines containing "0x8189". Change both to "0x8198" instead...)
               Step 6. Now here is the problem... when i used this command sudo ./makedrv. I got two errors,but it is also mention there that "Ignore the swathes of warning messages." so i used to ignore it. but when i come at step 7 there was a big blunder

              Step 7: Load the driver using sudo ./wlan0up.
and I got the following problems... while executing step-7:

insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

and then i also ignore this , and carry on with the next steps, but it did nt work, but i feel the problem is right at step 7, i tried again and again... but still same problem, Now please let me know, where is the problem???

---

### Post by mali2 on 2008-12-31
The specific problem has been solved ,Just check out the last thread of following link... you will get the solution....>>>>>>>>>
[http://ubuntuforums.org/showthread.php?t=1022311](http://ubuntuforums.org/showthread.php?t=1022311)

---

