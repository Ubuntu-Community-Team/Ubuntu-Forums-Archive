---
title: "Tascam US-122 + Ubuntu Studio"
date: 2009-01-03
forum: Multimedia Software
---

### Post by Geo_V on 2009-01-03
Hi, 

I am new to Linux and istalled Ubuntu, which i found very attractive and would like to gradually make it my default operating system. However, i am facing a serious problem with my soung card "Tascam US-122" which can't be installed. I've read a few topics on the Internet saying that it can be installed and showing the way, but no matter how much i tried, i could not get it to work. I then installed Ubuntu Studio, but still with no success. This is a serious matter for me, being a musician, so if anyone actually "HAS" managed to install it, i would be very interested in knowing how. Hope someone has the answer.

Thanks,
George

---

### Post by Geo_V on 2009-01-03
I tried the installation i found on the following page 

[https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

The Server at Step 2 could not be found as my terminal said, so i downloaded the rpm file from this ftp site manualy 

[http://www.filewatcher.com/m/alsa-firmware-1.0.9-4.noarch.rpm.1309295.0.0.html](http://www.filewatcher.com/m/alsa-firmware-1.0.9-4.noarch.rpm.1309295.0.0.html)

and continued the proccess. Everything goes on well but when I reach Step 9 and try to load the sound card i recieve the message:

" no US-X2Y-compatible cards found "

Hope this piece of information helps somebody to guess the solution.

---

### Post by Geo_V on 2009-01-03
These are the results of the lsusb command just before Step 8 :

**Bus 005 Device 010: ID 1604:8007 Tascam _US-122 Audio/Midi Interface_**
Bus 005 Device 005: ID 145f:015a  
Bus 005 Device 004: ID 152e:2507 LG (HLDS) 
Bus 005 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I then run the following command:

sudo fxload -s /home/x-pc2/usx2y-fw-0.1b/ld2-ezusb.hex -I /usr/share/alsa/firmware/usx2yloader/us122fw.ihx -D /dev/bus/usb/005/010

and then the "sudo usx2yloader" command which gives me the " no US-X2Y-compatible cards found" message. At this point also the "lsusb" command the results are :

Bus 005 **_Device 011_**: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 005 Device 005: ID 145f:015a  
Bus 005 Device 004: ID 152e:2507 LG (HLDS) 
Bus 005 Device 003: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I don't know, is this difference at the Device number right?

---

### Post by Geo_V on 2009-01-04
Any Help Please....????:confused:

---

