---
title: "Wireless no longer works after upgrade to 13.04"
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by jca2323 on 2013-04-25
Hi. I recently upgraded to 13.04 and my wireless no longer works. iwlist scan wlan0 shows my wireless network but native ubuntu nor wpa supplicant will connect to it. I had it configured to join the network when it starts up by adding certain lines to the interface in /etc/network/interfaces but these don't work either,

---

### Post by wildmanne39 on 2013-04-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

