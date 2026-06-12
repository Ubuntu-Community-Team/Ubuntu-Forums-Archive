---
title: "Eee Box B202 WiFi Driver Installation Problems"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by alexlafreniere on 2009-08-25
I have an Eee Box B202 and I'm trying to get the wireless to work in Xubuntu. It has a Ralink rt2860 wireless card. I tried getting the Windows drivers working in ndiswrapper, and had been working off of these two threads:

[http://ubuntuforums.org/archive/index.php/t-1071580.html](http://ubuntuforums.org/archive/index.php/t-1071580.html)
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

I tried following the directions in the second thread, but every set of drivers I could find was deemed unextractable by the unzip program. So theoretically all I would need is the files contained inside those executables and I would be golden. But I even tried running the driver executables inside Windows and getting the files from there but I couldn't find the right ones. After a bit of Googling I found this:

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Native Linux drivers from the manufacturer! And they're open source! But I couldn't figure out how to install them. I (maybe wrongly) consider myself proficient compiling software in Linux, but the readme was gibberish to me. So if anyone could help me compile and install these drivers, that would be much appreciated.

---

### Post by alexlafreniere on 2009-08-25
Just a quick bump. Anyone got any experience compiling drivers from source?

---

### Post by chili555 on 2009-08-25
Can you walk the laptop over to the router and connect an ethernet cable and open a terminal and do:```
sudo apt-get install build essential
```Then, assuming the file is on your desktop, do:```
cd Desktop/2009_0521_RT2860_Linux_STA_V2.1.2.0/os/linux/
gedit config.mk
```Where it says *HAS_WPA_SUPPLICANT=n*, change it to *HAS_WPA_SUPPLICANT=y*. Where it says *HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n*, change it to *HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y.* Proofread, save and close gedit. Now do:```
cd ~/Desktop/2009_0521_RT2860_Linux_STA_V2.1.2.0/
sudo make

```If you have no errors, then do:```
cp RT2860STA.dat /etc/Wireless/RT2860STA/RT2860STA.dat
sudo make install
sudo modprobe rt2860sta
```Your wireless should spring to life. Post back if you hit a snag.

---

### Post by alexlafreniere on 2009-08-26
When I ran this command:

```
cp RT2860STA.dat /etc/Wireless/RT2860STA/RT2860STA.dat
```

I got this error:

```
cp: cannot create regular file `/etc/Wireless/RT2860STA/RT2860STA.dat': No such file or directory
```

I even tried running it with sudo and got the same error. Should I create etc/Wireless manually?

---

### Post by alexlafreniere on 2009-08-26
Just a quick note, I'm using Xubuntu, not Ubuntu, although that shouldn't matter much.

---

### Post by alexlafreniere on 2009-08-26
Got it to work! Just a couple gotchas:

1. Had to create /etc/Wireless and it's subdirectories manually. cp command won't, most likely because it's a critical system directory.

2. Had to set up a connection with my network manually. For some reason autodetection of networks is either off or doesn't work. Just enter in your SSID and you're good to go.

Thank you so much chili555, you saved the day!

---

