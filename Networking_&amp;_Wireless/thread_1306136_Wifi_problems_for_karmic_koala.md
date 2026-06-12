---
title: "Wifi problems for karmic koala"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by naveevolution on 2009-10-30
I have been using Jaunty for sometime and everything worked from the word go. But when I upgraded my system to karmic koala my wifi stopped working. It says no networking device found. I have a toshiba satellite L310. My wireless card is an Atheros AR5001. Everything else works. So please guys any help will be most appreciated.

---

### Post by pi4r0n on 2009-10-30
Have you tried any of [this]("http://ubuntuforums.org/showthread.php?t=885847")

Remember karmic koala is still Ubuntu nothing major have changed so solution is going to be almost the same one.

Ta

pi4r0n

---

### Post by fskaw on 2009-10-30
This worked for me for Karmic. My wireless card is also an Atheros AR5001.

Open a terminal and insert:

sudo modprobe ath5k

---

### Post by naveevolution on 2009-10-30
> **fskaw said:**
> This worked for me for Karmic. My wireless card is also an Atheros AR5001.

Open a terminal and insert:

sudo modprobe ath5k

Tried it but nothing.

---

### Post by fskaw on 2009-10-30
Try this from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395565](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/395565) . ALso see further advice in the thread. Below is the one that might work for you.


"
Confirmed bug on Toshiba A135-S2386 using "02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)" and 2.6.31-2-generic

There are two method of enabling/disabling the wireless on this laptop:
   1. softkey Fn+F8
   2. toggle switch on the front of the laptop (with LED indicator)

After booting:
Method 1 does nothing. Method 2 does nothing. The following modprobe method listed by itchy8me enables the wireless:

sudo modprobe -r -f ath5k
sudo modprobe ath5k

After this, method 1 does nothing (does not enable/disable wireless). Method 2 operates as it should, it disables the wireless (cannot ping google.com). However, the icon in the upper panel does not indicate the wireless is disabled. I added a shell script with the commands listed above to get wireless working
"

---

### Post by naveevolution on 2009-10-31
Tried both methods but still no result. I dont understand this, it was perfect in Jaunty why on earth did the ubuntu guys have to mess with it.

---

### Post by drpjkurian on 2009-11-01
> **naveevolution said:**
> Tried both methods but still no result. I dont understand this, it was perfect in Jaunty why on earth did the ubuntu guys have to mess with it.


Hi

Please visit my thread 
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
It might help you.

Best of luck
Dr kurian

---

### Post by quackking on 2009-11-01
I have a Compaq CQ60-210US notebook (dual-core AMD 64, with a pushbutton WiFi switch located next to the power button above the keyboard.) It has an Atheros AR5001 Wifi adapter (AR242x chipset) using ath5k driver in 2.6.31-14-generic kernel. I am using the 185-series nVidia driver.

Wifi did not work. I kept seeing this sort of thing in dmesg:

'WLAN0 device not ready' usually preceded by a reference to 'forcedeth' a second or two earlier.

Being a dunce, I decide to get rid of forcedeth by brute force (heh - death to forcedeth?) That did nothing.


However, installing 

linux-backports-modules-headers-karmic-generic
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

and doing a cold start did work. Now nm-applet works, showing available wireless networks and also wired networks. Plugging, unplugging, connecting, disconnecting - all work. 

 YMMV.

---

### Post by naveevolution on 2009-11-01
> **quackking said:**
> I have a Compaq CQ60-210US notebook (dual-core AMD 64, with a pushbutton WiFi switch located next to the power button above the keyboard.) It has an Atheros AR5001 Wifi adapter (AR242x chipset) using ath5k driver in 2.6.31-14-generic kernel. I am using the 185-series nVidia driver.

Wifi did not work. I kept seeing this sort of thing in dmesg:

'WLAN0 device not ready' usually preceded by a reference to 'forcedeth' a second or two earlier.

Being a dunce, I decide to get rid of forcedeth by brute force (heh - death to forcedeth?) That did nothing.


However, installing 

linux-backports-modules-headers-karmic-generic
linux-backports-modules-karmic
linux-backports-modules-karmic-generic
linux-backports-modules-wireless-karmic-generic

and doing a cold start did work. Now nm-applet works, showing available wireless networks and also wired networks. Plugging, unplugging, connecting, disconnecting - all work. 

 YMMV.


Tried it and the one above still nothing. I couldn't wait for karmic to come out thinking it would be better than jaunty. Jaunty used to change my resolution everytime I start up my laptop. With Karmic that was resolved but my wireless card stopped working. Now I'm running on a D-link wireless usb adapter to connect to the internet. I'm thinking of switching back to Jaunty and waiting for this bug to be fixed before switching back.

---

### Post by johnbyrne on 2010-02-14
I had these same problems. I had created a user called 'student' and had no wireless access from this user. The 'modprobe' solution worked for my 'admin' account, but this user blocked all my attempts to fix it that way.

Eventually I figured it mayyh have to do with privileges and checked the properties of the user. Bingo! I enabled the privilege 'connect to wireless networks', restarted and Voila!  It works!

---

