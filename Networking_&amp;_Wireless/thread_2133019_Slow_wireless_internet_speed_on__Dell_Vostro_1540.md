---
title: "Slow wireless internet speed on  Dell Vostro 1540"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by samdeniyi on 2013-04-06
[COLOR=#000000][FONT=arial]I am using Linux (Ubuntu 12.04 LTS) for the first time, I installed it along side windows 8 but the internet speed on ubuntu is die too slow, can some help with a hint of how to go about improving the internet speed. not evening opening web pages. I did the installation on  Dell Vostro 1540. thanks in advance  [/FONT][/COLOR]

---

### Post by wildmanne39 on 2013-04-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

