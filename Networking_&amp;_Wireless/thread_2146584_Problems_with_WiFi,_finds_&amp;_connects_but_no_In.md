---
title: "Problems with WiFi, finds &amp; connects but no Internet"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by Mahogan on 2013-05-19
I just did a fresh install of Xubuntu 13.04 on my desktop.  I use a Rosewill RNX-N180UBE usb wifi.  When installing it found the wifi and router, it connects, but would not download anything.  I rebooted and did the install with the wifi unplugged so that I could get the OS installed.  Now when starting, it does show all available routers, I can connect to mine, but still no internet.  When viewing the Network Connection, it shows that I am connected and the Driver is: r8712u.  Still no internet.  

My desktop is a dual boot, Win7 and Xubuntu.  In Win7 the internet works perfectly.

I went to the Rosewill Site and see that it is possible to download a driver for Linux Kernal 2.6.18~2.6.38 and Kernal 3.0.2.  I downloaded these on my laptop to a usb stick and copied the file to my desktop in the home/ubuntu/downloads/ folder.  I do not know how to install them.  The file is a tar.gz

Can anyone tell me if I need to install these other drivers and if so, how?

Or if there is something I can do with the default Xubuntu driver for this, or if there is something else to get internet?

Thank you in advance!

---

### Post by Mahogan on 2013-05-19
I have just been doing some experimenting with this. When I open Firefox and go to google, it will load google, all loads but the logo, then when searching for something, it give me no internet connection message.   Then when doing an Ubuntu update, it will download the first small file then drops the connection and hangs.

So it seems there is some connectivity, but then it drops it.  Sounds like a driver glitch to me, but I am not sure.  Can someone please advise?

---

### Post by Hadaka on 2013-05-19
Hi, did you do the updates and upgrades after you loaded the os?
from a wired connection please do..

```
sudo apt-get update
sudo apt-get upgrade
```
if you have not done this..be patient..it may take some time.
please also post the output of..
```
lsusb
```
the driver may already be in the kernel.
finally..here is a link with the same usb you have.
[http://ubuntuforums.org/showthread.php?t=2095623](http://ubuntuforums.org/showthread.php?t=2095623)
good luck

---

### Post by Mahogan on 2013-05-25
Okay, I finaly had a chance to hook this up wired as suggested.  Here is the result of lsusb

```
ubuntu@ubuntu-TH67B:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 004: ID 0a05:7211  
Bus 002 Device 005: ID 2222:3075 MacAlly 
Bus 002 Device 006: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 007: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
ubuntu@ubuntu-TH67B:~$
```

When I did the update it seemed to crash, after about three hours the progress bar was about 3/4 complete, and was non responsive with the HD light solid for the whole time.  I finally hit the reset button and it went back into Xubuntu and all seemed fine (with the exception of no internet, even though it shows it is connected wirelessly).  I opened Chromium and it gave me a black screen and said something about panic?  I rebooted and it loaded did a disk check and said there was an error and I told it to Fix it, now it seems to run okay.  This is a triple boot system.  I first had Win XP then loaded Ubuntu 10.04, it all worked fine on a wired connection, then I moved the computer beyond the length of my wire and bought the USB Wifi and it never did work in Ubuntu 10.04.  So I lived without Ubuntu and just used WinXP, then I upgraded to Win7 and added a new partition to Triple Boot, and then Tried Xubuntu CD and my wireless seemed to work fine, so I deleted the Ubuntu 10.04 partition, recreated new and installed Xubuntu and now the Wifi does not work, just as before with 10.04.

---

