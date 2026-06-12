---
title: "confused about connection wireless with v13"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by cara-phonecoop on 2013-08-25
Hi,
Can anyone offer simple instructions for connecting to wireless with ubuntu 13?  I could connect ok when with hardy heron but now the menus look different and I can't see anything that I recognize.  Thanks!
C

---

### Post by wildmanne39 on 2013-08-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

