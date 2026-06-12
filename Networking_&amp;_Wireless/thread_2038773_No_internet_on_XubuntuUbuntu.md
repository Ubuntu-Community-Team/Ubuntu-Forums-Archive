---
title: "No internet on Xubuntu/Ubuntu"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by Vanatiq on 2012-08-07
Hi, I´ve tried to install both Xubuntu and Ubuntu with the wubi-installer from ubuntu.com. The installation went fine both times, however I couldn´t get the internet up and going on either of them. Not even wired... 

The laptop is an old HP Compaq 6735b, and the card is a: **Broadcom 4322AG 802.11a/b/g/draft-n -card for wireless network**

The computer has a **touch** button for toggling wireless on and off.  In Windows, the button is working without problems, and I also have internet (both wired and wireless) in Windows. When I launch Ubuntu or Xubuntu, the button is orange which means it´s turned off. No matter how much I click it, it won´t turn on. The button is only for wireless, and as the wired isn´t working either, I´m thinking that it´s because I need to download drivers?

I´ve searched around for a while, but all the topics were old and the links in them were broken. Here´s one of them: [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Does anyone know if the problem is lack of driver and are there any tutorials for manually installing them on Ubuntu/Xubuntu?

Thanks in advance

---

### Post by wildmanne39 on 2012-08-07
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by Vanatiq on 2012-08-07
> **wildmanne39 said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/netscript.sh && chmod +x netscript.sh && ./netscript.sh
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

I don´t even get the wired to work on it, so that´s gonna be a bit difficult :P Can I download it on another PC and transfer it over manually and then run a command in the terminal to execute it? If so, do you have a command for only running the script?

---

### Post by wildmanne39 on 2012-08-07
Hi, installing the driver is harder without internet.

Please go to this link and follow the directions for installing the sta driver with the internet.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Thanks

---

