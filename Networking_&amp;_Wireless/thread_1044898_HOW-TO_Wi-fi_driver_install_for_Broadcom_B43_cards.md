---
title: "HOW-TO: Wi-fi driver install for Broadcom B43 cards"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by Felliph3 on 2009-01-19
Hello, I have always struggled getting wi-fi to work on Linux in general. Since I'm always installing other distros back and forth on my crappy Acer Aspire 5000 series, its always a struggle to get wi-fi to work on it. This is a how to for the B43 cards. I have the B4318 but it could work for your B43. I'm putting this thread together from the help of user Ayuthia from his replies in previous threads. This method got me online in less than 3 minutes and this is on a live cd and doesn't even require restart. 

This is geared toward beginners to Ubuntu so I have a summarized version at the bottom for the more experience users. Here we go!



**1)**First off, you need the b43-fwcutter package installed. If you don't have internet you have these 2 options:

**A)** Log on to windows or whatever operating system you have on the same computer that has wi-fi working and go to this link and download the package, I have the i386 architecture so I chose that, but you may use the amd64 if thats what you have. Save the file to the desktop.

[http://packages.ubuntu.com/hardy/utils/b43-fwcutter](http://packages.ubuntu.com/hardy/utils/b43-fwcutter)

**B)** Go to a computer that has internet working and save the b43-fwcutter package to a USB drive. Once again pick the corresponding architecture, amd64 or i386.

[http://packages.ubuntu.com/hardy/utils/b43-fwcutter](http://packages.ubuntu.com/hardy/utils/b43-fwcutter)





**2)**That package extracts the firmware for ya. Now you need the firmware. You can get it here, do the same as above, save it to the desktop or on a usb drive.

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)
 




**3)** Now boot into Ubuntu. You will need to put those 2 files on the Home directory.

**A)** If you saved them on the desktop of that computer, then you need to mount the drive that its on so go into PLACES on the upper taskbar and click on it. It is usually bigger drive. Now open it and if you have windows you will have to go to documents and settings>>"your user name">>Desktop and thats the Windows desktop. So drag and drop those 2 files to the Home folder which is under PLACES. While you have the desktop folder open, double click to open the b43-fwcutter .deb file. This will install it. Say no to fetch firmware.You can then close that folder.

**B)** If you saved them onto a USB drive, then just go to PLACES on the upper taskbar and open the HOME folder. Drag and drop the files there. While on the USB drive folder, double click to install the b43-fwcutter.
Say no to fetch firmware.




Now that we have the firmware in the home folder and b43-fwcutter package installed you need to open the terminal to extract the firmware using b43-fwcutter. You can open the terminal under APPLICATIONS>>ACCESSORIES on the top taskbar.



Now copy and paste each command on the terminal at a time. You can copy by selecting the text below and CTRL+C and pasting on the terminal with CTRL+SHIFT+V.


Code:

> cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

tar xfvj broadcom-wl-4.80.53.0.tar.bz2

sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

sudo ifconfig wlan0 up





Hopefully after about 30 seconds of this you should be seeing wifi networks! Let me know if it worked for you guys or if you have any questions. Thanks.
> [B]
Summarized version:[/B]

Download b43-fwcutter:

[http://packages.ubuntu.com/hardy/utils/b43-fwcutter](http://packages.ubuntu.com/hardy/utils/b43-fwcutter)

Download 2 files of firmware:

[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Open the b43-fwcutter file to install it. Now drop the firmware on the HOME folder.

Go into the terminal and paste each line at a time and you're golden!


Code:

[QUOTE]cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o

tar xfvj broadcom-wl-4.80.53.0.tar.bz2

sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy

sudo ifconfig wlan0 up

[/QUOTE]

NOTE:The broadcom-wl-4.80.53.0 firmware changes to broadcom-wl-4.150.10.5 in 2.6.25 (Intrepid and newer).

I think that the older firmware should work in Intrepid, but they will get a warning about it being old firmware that will lose support. It should still work though.

Thanks everyone for reading and I hope I did a good job on my first Linux tutorial. Thanks Ayuthia as well for making that code for me last year haha! :guitar:

---

### Post by gsergey on 2009-12-03
I'm so glad I didn't give up and ..... found this post :)))
It's my first time with Ubuntu, on Compaq nx6110, couldn't get wireless working...
At the end, after doing all the above, still had to do one extra step: System: Administration: Windows wireless drivers.
Thanks! :P

---

### Post by Felliph3 on 2010-11-19
Glad I could be of help!

---

### Post by lixiao on 2013-02-19
Thank you so much! I have been looking for a solution for many days. Finally your way solved my problem!

---

