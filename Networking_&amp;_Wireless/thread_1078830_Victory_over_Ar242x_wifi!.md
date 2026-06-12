---
title: "Victory over Ar242x wifi!"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by diamondjim08 on 2009-02-23
There is victory over the Atheros AR242x wifi onboard the Acer 5515 Laptop!
This is for the 32 bit system, here is how:
1. Make sure you have a clean, new install of Ubuntu.  My error was trying to install this wifi after an install that was "added to" with other software.  Immediately after the CD install and the updates have been added, work on the wifi.
2. Go to /etc/modprobe.d/blacklist in the terminal and type
sudo gedit (terminal will ask you for your password).  The system will now allow you to edit the blacklist file and save it.
3. Add the following lines to the bottom of the file:
blacklist ath_pci
blacklist ath_hal
Reboot your machine.
This will prevent these drivers from interfering with this wifi install. Trust me, they are on the machine so do it.
4. Go to Synaptic installer found in System/Administration/Synaptic and open it.  After the packages are displayed, type "ndiswrapper" in the search box.  Mark for installation and install the files Synaptic lists to install.
5. After ndiswrapper is installed, go to System/Administration/ and at the bottom of the list you will see "Windows Wireless Drivers".  This is the ndiswrapper program that will install the driver for AR242X wifi.
6. Download the driver "xp32-5.3.0.56-whql.zip from [http://download107.mediafire.com/2gylsbcrgttg/njmdytwnqjz/xp32-5.3.0.56-whql.zip](http://download107.mediafire.com/2gylsbcrgttg/njmdytwnqjz/xp32-5.3.0.56-whql.zip) to your new desktop.  Double click to expand the files to Desktop.
7. Open "Windows Wireless Drivers" found in Administration and browse to your desktop and find the net "net5211.inf" driver and click on it to install.
8. Check wifi icon and miracles of miracles, it works!!!!!!!!!!!:D
I'm not exactly stupid BUT I spent a lot of time trying to install this wifi with madwifi, compat-wireless and ndiswrapper (the first time). This was the cleanest and most direct method. I also had the expert help of several very talented people who were very gracious with their time and help on this forum.  So many thanks to them for their efforts!!

---

### Post by Crafty Kisses on 2009-02-23
I remember I helped you on this issue, and I'm really glad I could assist you in getting this issue fixed, congratulations and thanks for posting this up! It will sure help more people in the future.

---

### Post by diamondjim08 on 2009-02-24
Hi Codename,

Thanks again for your help with this.  BTW, prior to success with this wifi problem, the Ubuntu install was done via WUBI which worked well.  However, in the process of installing all the "Multimedia & Video How to" and then trying to install the wifi,  I must have introduced a wild hair into the system.  So in the order of important and in the interest of saving much time, I would recommend that anybody who has a wifi should install this before any other OS enhancements are done.
Thanks again for help and dedication with this very excellent OS!
<> Jim

---

### Post by Reiger on 2009-02-24
Ndiswrapper should not be neccesary with Ubuntu 8.10, and it will save you quite a few reboots on a laptop if you can get ath5k to work instead. (Which should with a clean 8.10 be as easy as installing the backports and adding the ath5k line to /etc/modules, using ```
echo "aht5k" | sudo tee - /etc/modules
```.)

The reason why I would advocate spending a little to a lot more time on getting ath5k to work is that ndiswrapper is very weak at connection-loss scenario's. Granted, if you have WICD you may be able to get by that in ~90% of the cases using a custom unload/reload script ... still it is more reliable and probably faster to work with ath5k instead. It is particularly obnoxious in a WPA-PSK type of network which requires both router and client to remain in sync (because the actual WPA key is different each session, so it will bork if your router thinks you're not online whereas your ndiswrapper is unaware that you are not). Also: switching from ESSID and the like is a pain in ndiswrapper -- but works flawlessly with native drivers.

---

### Post by diamondjim08 on 2009-02-26
HI Reiger,

Where were you when I needed you! :-) certainly your code looks simple enough and if I had it at the beginning would have tried it.  So far, ndiswrapper is working very well and the only time there are dropped connections is with very weak signals.  Otherwise no problem.
I will keep your code handy in case there are problems.  Thanks for your feedback - this is the way I learn.
<> Jim

---

### Post by Bones80 on 2009-02-26
Running Toshiba laptop, wireless worked well in kernel 24-18, when I upgraded to 24-22 it quit. I only see wired connection. Help!

---

### Post by Crafty Kisses on 2009-02-26
> **Bones80 said:**
> Running Toshiba laptop, wireless worked well in kernel 24-18, when I upgraded to 24-22 it quit. I only see wired connection. Help!

You could try reverting back to the older kernel, or see if the wireless card is even recognized by running the following:
```
lshw -C network
```

---

