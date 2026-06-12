---
title: "asus usb-n66 install help"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by john32 on 2013-08-04
im pretty new to linux and ubuntu i could use some help.  I have an asus usb n66 wifi adapter i would like to use but i have no idea how to install tar.bz2 files.  any help would be greatly appreciated.  thanks

---

### Post by wildmanne39 on 2013-08-04
Hi, make sure your adaptor is plugged in then copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by john32 on 2013-08-04
thanks for the help

---

### Post by wildmanne39 on 2013-08-04
Hi, you posted the actual script we need to see the file it created, it will be called wireless-info.tar.gz or netinfo.txt in your home folder.
Thanks

---

### Post by john32 on 2013-08-04
i just realized that i ran the script with the asus adapter plugged in ( the one i want to use) but i also had my netgear plugged in also. the netgear is what i have connected to the internet to i need to re run the scrip or will that work?

---

### Post by wildmanne39 on 2013-08-04
It would be best with just the adaptor plugged in that you are trying to get to work, also please see post 4.
Thanks

---

