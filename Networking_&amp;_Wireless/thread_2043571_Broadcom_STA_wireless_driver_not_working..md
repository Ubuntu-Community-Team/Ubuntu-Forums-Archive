---
title: "Broadcom STA wireless driver not working."
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by Maradde on 2012-08-16
I already tried what says on many posts around here and its still not working. I have an Acer Aspire d250 and just got ubuntu, i had never used any linux version before so please be patient.
Any help would be veryy appreciated.
Thanks!

---

### Post by wildmanne39 on 2012-08-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

