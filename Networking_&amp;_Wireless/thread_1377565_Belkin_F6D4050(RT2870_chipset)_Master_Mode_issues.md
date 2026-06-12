---
title: "Belkin F6D4050(RT2870 chipset) Master Mode issues"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Matand009 on 2010-01-10
Hello, I'm trying to make a access point for my nintendo dsi's and my wii on my computer running linux.  It's running Ubuntu server 9.10, meaning no gui for me :P

As mentioned in the title, I have a Belkin F6D4050 usb device which has a rt2870 chipset and master mode should work.

I have build the latest version of ralink's driver from source and have got the device picked up.  

The problem is, when I run this command "sudo ifconfig ra0 down && sudo iwconfig ra0 mode master" I get the following error...

     Error for wireless request "Set Mode" (8B06):
          SET failed on device ra0; Network is down.

Originally to diagnose I ran "dmesg | grep ra0" there was an error like this: "no ipv6 router found" but since I have disabled ipv6 that error has gone.  

It's a weird error, that I'm unable to solve by myself.. I have already spent a few days on this :(.  And need to get my dsi online and updated now! lol.  

anyone with suggesting of things to try to get this working?

---

