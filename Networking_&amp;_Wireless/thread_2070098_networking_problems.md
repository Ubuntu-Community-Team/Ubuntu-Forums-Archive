---
title: "networking problems"
date: 2012-10-12
forum: Networking &amp; Wireless
---

### Post by elsontimana on 2012-10-12
hello people, i have some problem here, i installed ubuntu 12.04 LTS, but when the installation finished wireless doesn't work.
can you give me the solution? please

my laptop reference is:
laptop hp g5000   

hugs

---

### Post by wildmanne39 on 2012-10-12
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

