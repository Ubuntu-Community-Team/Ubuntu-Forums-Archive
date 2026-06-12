---
title: "broadcom bcm4306 not working"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by jtmedin on 2012-11-05
Had this trouble several os's ago & cant remember what i had to do to fix wireless. Help

did: lspci -nn

got: ... Broadcom corp BCM4306 802.11b/g wireless lan controller ...

---

### Post by jtmedin on 2012-11-06
Bump

---

### Post by wildmanne39 on 2012-11-06
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2012-11-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by rsavage on 2012-11-07
Just follow the wiki instructions [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by jtmedin on 2012-11-07
ok thanks, legacy did it. Now to figure out how to say solved.
BTW it was a bcm4306 version 2

---

### Post by jtmedin on 2012-11-07
thanks for the comeback, i had 2 choices & the first worked :-)

---

