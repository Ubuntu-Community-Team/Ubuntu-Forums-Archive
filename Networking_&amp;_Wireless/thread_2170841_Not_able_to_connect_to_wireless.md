---
title: "Not able to connect to wireless"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by dcs8240 on 2013-08-27
Hi everybody, I am a new user to Ubuntu. I have a dell inspiron 2200 that I just converted from xp to Ubuntu 12.04, and can't get wireless to find a network. I am able to connect by cable.  I have a bcm4309 wireless card which is supported. I have installed b43  FM-cutter as well as firmware.   In the terminal when I type rfkill  I get

command:
help
event 
list [indentifier]
block indentifier
unblock indentifier


when I type in iwconfig 

Lo:  no wireless extensions

eth0:  no wireless extensions 


Any help would be greatly appreciated.

---

### Post by wildmanne39 on 2013-08-27
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wildmanne39 on 2013-08-27
You can try this command with an internet connection:
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
if it does not work then run the script in my first post.
Thanks

---

### Post by jesus_montes on 2013-08-28
this works for me !
I have an hp pavilion dv2000 with Ubuntu 12.04.3 
Thank you !

---

### Post by jesus_montes on 2013-08-29
Hi again!,
I use this
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43

But every time I turn on my laptop I have to put it in a terminal, 

Do you know how can I start my laptop with the driver running ?

This is for avoid evry time run my terminal and install it again.

Thanks!

---

### Post by GwL3eNC on 2013-08-29
Hi, i believe it's only the sudo modprobe b43 which is lost on every reboot. You can add the modul
b43 in the /etc/modules file (as sudo).

---

### Post by wildmanne39 on 2013-08-29
jesus_montes this should work:
```
sudo su 
echo b43 >> /etc/modules 
exit
```
Thanks

---

### Post by dcs8240 on 2013-08-29
To Wildman:   installing the Linux non free firmware worked.  Thank you for your suggestions.  Have a great rest of the week.

---

### Post by wildmanne39 on 2013-08-29
Glad it worked!
Enjoy

---

