---
title: "Wireless not working 12.04"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by grman401 on 2013-07-16
Yes i have a Gatway 6020GZ and installed ubuntu 12.04 and my wireless is not showing any connections so i assume that the drivers and not installed..what do i have to do to get wireless working!? im very new to ubuntu so please bare with me!

---

### Post by grman401 on 2013-07-16
i really need the help..have no clue what to do and am using a friends computer...

---

### Post by wildmanne39 on 2013-07-16
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by grman401 on 2013-07-16
i hope this is what you need...did the exactly what the post said!

---

### Post by wildmanne39 on 2013-07-16
Please do:
```
sudo apt-get install linux-firmware-nonfree
```
Reboot

---

### Post by grman401 on 2013-07-16
forgot to mention it was the non-ethernet way...

---

### Post by wildmanne39 on 2013-07-17
Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

```
Thanks

---

### Post by grman401 on 2013-07-17
wont let me keeps saying file exsists..i extracted the file b43 to desktop and it wont let me copy past all of the code it just does the first line...then askes for my password

---

### Post by wildmanne39 on 2013-07-17
Type your user password it will not show as you type it then hit enter.

---

