---
title: "help with re-installing wi-fi"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by super newbie on 2013-05-25
hi all  i just did a fresh install of 12.04 and i'm having trouble with setting up wifi.  last time i did a fresh install was 10.04 (i think) and all i had to do was install ndiswrapper and go to the applications folder, then windows device driver (which had a GUI) and select the driver i wanted to use.  i still have the driver (Broadcom_bcm43xx_USB_32_64bit_V2)  my wireless USB adapter is a Netgear WNA3100.  also when i type "ndiswrapper -l" into terminal i get bcmn43xx32 : driver installed.  i think i have eveything i need but i just can't make it work......any ideas.   thanks

---

### Post by CodyLeeK on 2013-05-25
Grab an Ethernet cable, and hook it up to the computer and router.
When you have a Wired Connection Established message, go into System Settings.
Click on Additional Drivers or something like that, and then do a check for drivers.
Your wireless adapter driver should come up, so install it.
Unhook from your router, and test the connection.

Need more help, let me know.

---

### Post by super newbie on 2013-05-25
thanks for the quick response.............but i did all that and ig got "no proprietary drivers are in use on this system"  any thoughts

---

### Post by CodyLeeK on 2013-05-25
> **super newbie said:**
> thanks for the quick response.............but i did all that and ig got "no proprietary drivers are in use on this system" any thoughts

After re-reading your post, I saw that you have a USB Wireless Adapter. But, as the PDF manual for that adapter, it said:
> Windows7, Vista, Windows XP Home, or Windows XP Professional. Some versions of Windows ask for the original Windows operating system installation files to complete the 
installation of the WNA3100 v1 driver software.

Therefore, this is not compatible.

[http://www.downloads.netgear.com/files/GDC/WNA3100/WNA3100_UM_11Dec09.pdf](http://www.downloads.netgear.com/files/GDC/WNA3100/WNA3100_UM_11Dec09.pdf)

---

### Post by josephmills on 2013-05-25
Are you sure that you need ndiswrappper ?  
can you open up the terminal (ctrl+alt+t ) and enter in 
```
lspci -vnn | grep [FONT=Ubuntu Mono, monospace][COLOR=#000000]0280 [/COLOR][/FONT]
```     

then find the numbers that are in the [] should be something like [14e4:4311] then paste that here or type it as it is only 8 to ten characters thanks

---

### Post by super newbie on 2013-05-25
let me be a little more clear  this is a USB wireless adapter that i have been using for about 3 years on my ubuntu box. i've always used ndiswrapper and the drivers i listed in my first post and its always worked.  i just did a fresh install of 12.04 to try and solve another problem i was having with my iphone.  i know it works.  i tried to type in "lspci -vnn | grep 0280" and got nothing, so i changed "lspci" to "lsusb" and got this
mike@mike-MS-7592:~$ lspci -vnn | grep 0280
mike@mike-MS-7592:~$ lsusb -vnn | grep 0280
lsusb: invalid option -- 'n'
lsusb: invalid option -- 'n'
Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program

---

### Post by josephmills on 2013-05-25
```
lsusb
```

is good on its own thanks, did not know that it was a usb :/

---

### Post by super newbie on 2013-05-25
mike@mike-MS-7592:~$ lsusb
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mike@mike-MS-7592:~$

---

### Post by josephmills on 2013-05-25
> **super newbie said:**
> 
Bus 001 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]


Take a look at post #3 on this link plz :) 
[http://ubuntuforums.org/showthread.php?t=1835175](http://ubuntuforums.org/showthread.php?t=1835175)

---

### Post by super newbie on 2013-05-25
it works.....thanks sooo much for your help, i've been going thru posts for almost a week, and you found the right post in only half an hour, can't thank you enough:D

---

