---
title: "Samsung Galaxy S2 not recognised in 11.04"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by dhkillian on 2011-07-17
Just upgraded to 11.04 Natty Narwhal, and got myself a Samsung Galaxy S2. 

Tried connecting via USB in order to sync contacts, photos etc. Got the error: 
"Unable to mount SAMSUNG_Android Error initialising camera: -60: Could not lock the device" 

Wanted to use the USB storage and USB tethering, so I enabled USB debug mode. So did this on the phone: 

Settings > Applications > Development > USB Debugging

Ubuntu can't see the phone. Then tried:

Settings > Wireless and Network > Tethering and Portable Hotspot Settings > USB Tethering.

Still no joy. Typing "lsusb" in terminal gives me:

derek@derek-Vostro-200:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 04e8:685e Samsung Electronics Co., Ltd 
Bus 002 Device 004: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 002: ID 050d:615a Belkin Components 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


So it sees it in lsusb, but nowhere else, so I still can't copy and sync etc.

Anyone come across this problem, and if so, how were you able to solve it. Really grateful for any help.

Kind regards

DHK

---

### Post by roberthanekom on 2011-07-20
Look at this:
[http://androidforums.com/samsung-galaxy-s2/339013-usb-connectivity-mac-linux.html](http://androidforums.com/samsung-galaxy-s2/339013-usb-connectivity-mac-linux.html)
Hope it helps!

---

### Post by lcdvirgo on 2011-10-16
I just solved this on my phone and copy files successfully. I'm using AT&T version Samsung Galaxy S2 and Asus K401J. 

Steps:
1. Go to: Settings &#10132; Wireless and network &#10132; USB utilities.
2. Connect your phone to your PC using a USB cable.
3. Tap Connect storage to PC.
4. Scroll down from the phone notification bar. Click USB Mass Storage and tap "Connect storage from PC". The android robot will turn from green to orange. (Important step!:D)
5. From your PC, open the folder to view your files.
6. Copy files between your PC and the memory card.

---

### Post by alzurzin on 2012-01-09
thank you!  does anyone know where the phone book is stored on the Samsung Galaxy S2 and how to copy it to a directory in ubuntu?

---

### Post by snikjou on 2012-02-14
you don't need to sync your contacts manually. install google sync and you'll have all the contacts from your phone in your google contacts.

---

### Post by Dngrsone on 2012-08-26
I have a Galaxy S II from Sprint model D-710, there is no option to mount as USB...

I get the camera error, and am unable to see the contents of folders.

Any more ideas?

---

### Post by Correl Freehand on 2012-11-28
Hey I was having this problem and found a work around not a fix.

1. open disk utility
2. unmount both the phone and sd card
3. mount them with disk utility

This will give them their own mount point instead of usbX mount point which keeps you from transferring files to and from.

Seems that the auto mount is not working correctly. I tried several times to do it the right way then decided to check to see if it was a problem with mount. Again this is a work around but a strange one for me at least. And yes I read all of these posts and tried them first before going with hardware fix instead of software fix. I figured the software was having a problem so go to the hardware settings and fix it that way.

Samsung Galaxy S2
Ubuntu (Studio Version) 11.10

---

### Post by LuisGMarine on 2012-11-28
What version of Android is the phone running?

---

### Post by Dngrsone on 2012-11-28
> **LuisGMarine said:**
> What version of Android is the phone running?

For me it's Ice Cream Sandwich-- 4.0.4

---

### Post by LuisGMarine on 2012-11-28
I have a Galaxy S3 with ICS, and ubuntu 12.10.  I haven't played around much with it, but I think I was able to copy some files to the internal memory and not the SD card.  I gave up on connecting the phone and just use an SD card adapter to transfer all my media files.

I followed this link, but I can't gurantee it will solve your problem but its worth taking a look at.  It seems the issue is this whole MTP thing that Android 4.0 > use.

[http://askubuntu.com/questions/169516/access-files-on-samsung-galaxy-s3-external-sd-card]("http://askubuntu.com/questions/169516/access-files-on-samsung-galaxy-s3-external-sd-card")

---

### Post by Correl Freehand on 2012-12-05
> **LuisGMarine said:**
> What version of Android is the phone running?
And for me it's Ice Cream Sandwich-- 4.0.4 Samsung Galaxy S2 Skyrocket
Desktop System Ubuntu Studio 11.10

---

