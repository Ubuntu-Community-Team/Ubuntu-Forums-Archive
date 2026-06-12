---
title: "Sierra Wireless 598u help please"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by brandimarch on 2009-04-14
Hello, I am new to using Ubuntu.  I have it on my Dell mini 12 and have a Sierra Wireless 598u.  I have it working with GNOME PPP and it works fine, however, when I reboot the system I have to go through the first three steps by opening up the terminal and using:

sudo modproble -r usbserial

sudo modprobe usbserial vendor=0x1199 product=0x0025

(then plug in the usb modem)

sudo dmesg|grep -i ttyusb

If I don't do this every time when I boot up, the GNOME PPP will not recognize the device.  I have no idea how to save this or add it into the bootup script...is there something that can be done?  Any help would be much appreciated.

Thanks,

Brandi  ;)

---

### Post by clinto on 2010-04-15
I'm trying to set up CrunchEee 8.10.02(Ubuntu based using OpenBox wm) on my boss' Eee PC 900 and she uses a Sprint 598u USB modem.  I've found a guide from sprint, but it has you using Kppp, which doesn't work in OpenBox.  I'm using gnome-ppp instead.

Sprint guide: [http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

I'm very much an amateur with networking altogether, and I've never really messed with these usb modems.  The differences between Kppp and gnome-ppp are enough to leave me a bit confused.  I've tried my best to guess using what information I could gather from the guide, but it's still not connecting.

I replied to this post because, like the author, I would too like to know how to set linux up to set these values at boot instead of entering them by hand each time(since my boss doesn't know anything other than point-and-click, and it's a bit tedious anyways).  I'm sure there is a config file that executes commands at boot or something.  Can anyone point me in the right direction?

---

