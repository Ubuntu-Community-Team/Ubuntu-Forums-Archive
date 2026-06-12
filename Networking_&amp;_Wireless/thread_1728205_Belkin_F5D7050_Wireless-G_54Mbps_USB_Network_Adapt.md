---
title: "Belkin F5D7050 Wireless-G 54Mbps USB Network Adapter Setup"
date: 2011-04-13
forum: Networking &amp; Wireless
---

### Post by Jason0885 on 2011-04-13
Thanks for reading.

**I know I put Belkin F5D7050 I meant Belkin F7D1101** Need to have this fixed please.


Okay, I recently installed the latest and greatest Lubuntu 64 bit, because I like lxde and I am planning a system migration. (I am really starting to not like windows 7.) I have some linux experience. I wouldn't say I am awesome at it, but I am comfortable trying anything. 

Example:
I have used CENTOS 5.6 to make a linux machine server as a glorified router, with asterisks, SIP, SSH server, x windows, GNome, VNC, and a user authentication system. and get this I walked somebody through setting this up over the phone. 

Anyways back to topic.

I reopened the root account (I honestly got tired of typing sudo every other command is the only reason why I opened it.) I plan on closing it after we are done.

lsusb lists the wireless adaptor

Wireless Card Link
[http://www.walmart.com/ip/Belkin-F5D7050-Wireless-G-54Mbps-USB-Network-Adapter/3756936]("http://www.walmart.com/ip/Belkin-F5D7050-Wireless-G-54Mbps-USB-Network-Adapter/3756936")

I have the driver CD.  
I installed ndiswrapper.
I copied the files from my driver cd to my <home> Directory. 
Then installed the Windows XP version of the drivers using *ndiswrapper -l <driver>*. 
I then made ndiswrapper force the driver to the vendor ID of the wireless card. Using *ndiswrapper -a <vendor ID> <Driver>*(I did this last night and the vendor ID escapes me. I am at work now.)
I finally ran *depmod -a* and *modprobe ndiswrapper*


I goto the windows wireless driver application, and it shows the driver as loaded and the hardware as found.

However, it still does not list a wireless device in the network manager to where I can connect to my wireless. iwconfig does not show any wireless LAN, but it is still listed in lsusb. Also, the light that shows activity on the wireless device does not light up or blink at all. I have about 6 usb ports on my desktop and have tried everyone. The wireless card also works in Windows 7 64-bit
 

On a strange side note. I do have internet access through LAN, (My laptop is atm a glorified wireless card lol.)


Any help would be appreciated.


*Edit 1*
I also plan on changing this into a how too once we get it figured out.

---

### Post by Jason0885 on 2011-04-13
/bump

---

### Post by Jason0885 on 2011-04-13
/bump #2

---

### Post by Jason0885 on 2011-04-14
*Update*

Printed off the ndiswrapper troubleshooting sticky
Went home yesterday
Went through troubleshooting sticky with lubuntu and ubuntu.

booted up Windows 7 64 bit, card works fine.

Unistalled Lubuntu 10.10 32bit
Installed Ubuntu 10.10 64bit

Reinsatlled ndiswrapper
Reinstalled driver

removed driver
Tried theese instructions modified it for my card.(This allowed me to turn on wireless but still couldn't see any networks and my card card still had no lights on it)
[http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101]("http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101")

Ran into this website
[http://www.wikidevi.com/wiki/Belkin_F7D1101_v2]("http://www.wikidevi.com/wiki/Belkin_F7D1101_v2")

Haven't got to try those drivers yet. I am getting them at the moment. Will try another fresh install of ubuntu. Will use 7zip to see if I can locate the driver files for 64 bit and try to get it working. 


lsusb still shows the device

lshw -C network
does not list a usb wlan card, Ethernet or anything like that. I have the print off saved at the house will upload them tomorrow.


Been almost a full day now and still no one is helping. I would appreciate anything.

---

### Post by Wolf_22 on 2011-05-03
I wish I had something positive to tell you, Jason. I tried those instructions you linked to and couldn't even get the the adapter to turn on. What all did you do to get THAT far?

---

