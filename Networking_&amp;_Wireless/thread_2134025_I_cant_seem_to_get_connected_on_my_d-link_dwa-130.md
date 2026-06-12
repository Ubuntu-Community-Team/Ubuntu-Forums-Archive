---
title: "I cant seem to get connected on my d-link dwa-130"
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by chrissy.millichamp on 2013-04-09
Ive purchased a network adapter d-link dwa 130, it works fine on windows 7 but wont work on Ubuntu 12.10, it always asks for my password when its correct. How do I install it?

---

### Post by Iowan on 2013-04-11
I get lost in the different security modes - which are you using?
I presume the adapter is working well enough to see your wireless router/access point...
(bump)

---

### Post by wildmanne39 on 2013-04-11
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

