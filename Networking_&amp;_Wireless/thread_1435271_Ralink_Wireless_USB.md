---
title: "Ralink Wireless USB"
date: 2010-03-21
forum: Networking &amp; Wireless
---

### Post by drizzay32 on 2010-03-21
I've installed all drivers and utilitys that are needed for the installation of my wireless USB but am unable to figure out how to get the card recognized. It's a Zonet ZEW2500P and I'm assuming it uses the rt2500 drivers. I am also wondering why my Red light flashes instead of being steady like normal.... Your help is greatly appreciated...Noobe

---

### Post by chili555 on 2010-03-21
Please open Applications > Accessories > Terminal and post:```
lsusb
iwconfig
lsmod | grep -e rt2 -e rt3
```The LED usually just blinks when the card is trying to associate with your router and not succeeding. When you click the Network manager icon, does it see your network? What happens when you try to connect?

---

### Post by drizzay32 on 2010-03-21
sumyungguy@sumyungguy-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
sumyungguy@sumyungguy-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 15a4:1336 Afatech Technologies, Inc. 
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sumyungguy@sumyungguy-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
sumyungguy@sumyungguy-desktop:~$ lsmod | grep -e rt2 -e rt3
rt2870sta             461875  0 
rt2800usb              31499  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27605  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204598  2 rt2x00usb,rt2x00lib
cfg80211              126645  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
sumyungguy@sumyungguy-desktop:~$ 

My wireless device has a red light and a yellow the red only flashes
When I connect it alone it trys to say connection established but of course unable to connect. Usually a 10.10. Ip

---

### Post by chili555 on 2010-03-21
> rt2870sta 461875 0
rt2800usb 31499 0
rt2x00usb 9703 1 rt2800usb
rt2x00lib 27605 2 rt2800usb,rt2x00usb
led_class 2864 1 rt2x00lib
mac80211 204598 2 rt2x00usb,rt2x00lib
cfg80211 126645 2 rt2x00lib,mac80211
crc_ccitt 1339 1 rt2800usbOh, my! How many drivers does it take to drive this thing? A lot fewer than you have. Please do:```
ls /etc/modprobe.d
```You may have a file in there called *blacklist* or one called *blacklist.conf*. If you have one called *blacklist*, do:```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
```If your file is called blacklist.conf, skip that step.

Next, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three new separate lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and let us know your result.

---

### Post by drizzay32 on 2010-03-21
When I get to the last step guide me thru the procedure for entering the 
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

---

### Post by chili555 on 2010-03-21
When you do this in a terminal:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open. Simply type in the three lines, proofread carefully, save and close gedit.

Please see attached.

---

### Post by drizzay32 on 2010-03-21
Did that but the jpg. that you sent I was unable to see it... Still unable to connect

---

### Post by drizzay32 on 2010-03-21
Ok,changed that getting ready for restart I'll let you know... Thanks

---

### Post by drizzay32 on 2010-03-21
Dude you are a GOD!!! I have almost tryed everything till this point... Thanks a million

---

### Post by chili555 on 2010-03-21
Thanks for your kind comments. Glad it's working and I hope we will have helped a few searchers.

---

### Post by M4xC4v413r4 on 2010-05-01
> **chili555 said:**
> Oh, my! How many drivers does it take to drive this thing? A lot fewer than you have. Please do:```
ls /etc/modprobe.d
```You may have a file in there called *blacklist* or one called *blacklist.conf*. If you have one called *blacklist*, do:```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
```If your file is called blacklist.conf, skip that step.

Next, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three new separate lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and let us know your result.

Thank you so much, had to change my router away from my desktop and the WirelessUSB was not connecting to the WLAN, it was &quot;seeing&quot; it but wouldn't connect, this fixed it.

---

### Post by keshvinder on 2010-06-12
hey guys, im having the same problem, ive been using xp for years now and i am a complete noob at ubuntu, soo if you can explain what to do step by step so that a beginner can understand, i will be greatly appreciative.

---

### Post by chili555 on 2010-06-13
> **keshvinder said:**
> hey guys, im having the same problem, ive been using xp for years now and i am a complete noob at ubuntu, soo if you can explain what to do step by step so that a beginner can understand, i will be greatly appreciative.Please be sure you have the same problem. Please open a terminal and do:```
lsmod | grep rt2
```If all these drivers are loaded:> rt2870sta 461875 0
rt2800usb 31499 0
rt2x00usb 9703 1 rt2800usb
rt2x00lib 27605 2 rt2800usb,rt2x00usb
led_class 2864 1 rt2x00lib
mac80211 204598 2 rt2x00usb,rt2x00lib
cfg80211 126645 2 rt2x00lib,mac80211
crc_ccitt 1339 1 rt2800usb Then do:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```

Add three new separate lines:
```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```

Proofread carefully, save and close gedit. Reboot and let us know your result.

---

### Post by hoangy on 2010-08-06
I had the same problem with the light flashing and it worked!  Thanks a bunch!

---

