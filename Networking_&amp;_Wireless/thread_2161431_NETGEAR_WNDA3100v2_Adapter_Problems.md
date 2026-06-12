---
title: "NETGEAR WNDA3100v2 Adapter Problems"
date: 2013-07-10
forum: Networking &amp; Wireless
---

### Post by bcariddi on 2013-07-10
Hello, I recently installed Ubuntu and **I need to get my wireless adapter (NETGEAR WNDA3100v2) to work with Ubuntu 12.04**. I cannot get a wired internet connection to the computer, but I can use a flash drive to transfer files from other computers if needed. I do have ndiswrapper installed, but I am not sure how to use it to install the files needed to use my adapter. I have the .inf file/files that is/are needed and my computer is a 64bit system. 
If you could help me get my adapter working, it would be a huge help! :D
Thanks in advance! :biggrin:

---

### Post by praseodym on 2013-07-10
Try this 64bit driver:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

Install it with
```

sudo ndiswrapper -i /path/to/64bit/INF-file
```
Change the router mode to "b+g" only

---

### Post by bcariddi on 2013-07-10
The file attached was not an .inf file, so the installation did not succeed. Is this the right file? Thanks.

---

### Post by praseodym on 2013-07-11
Unpack the tar.gz. There should be 2 folders...

---

### Post by bcariddi on 2013-07-11
Ohhh... Stupid me haha. 
Now the driver is installed, so what do I do next?
When I type ndiswrapper -l I get
```
bcmn43xx64: driver installed[INDENT]device (0846:9011) present
```[/INDENT]

---

### Post by praseodym on 2013-07-11
Reload the driver and re-plug the stick:
```

sudo modprobe -rfv ndiswrapper
sudo modprobe -v ndiswrapper
```
Check after that:```

iwconfig
dmesg | grep ndis
sudo iwlist scan
ifconfig -a
iwlist chan
```

---

### Post by bcariddi on 2013-07-11
sudo modprove -rfv ndiswrapper: ```
FATAL: Module ndiswrapper not found.
```
sudo modprove -v ndiswrapper: ```
FATAL: Module ndiswrapper not found.
```iwconfig: ```
eth0      no wireless extensions
lo        no wireless extentions
```
dmesg | grep ndis: nothing
sudo iwlist scan:```
eth0       interface doesn't support scanning
lo        interface doesn't support scanning
```
iwlist chan: ```
etho        no frequency information
lo        no frequency information
```

---

### Post by praseodym on 2013-07-12
Reinstall ndiswrapper:
```

sudo apt-get install --reinstall ndisgtk ndiswrapper-dkms dkms linux-headers-$(uname -r) build-essential
```

---

### Post by Egonosaur on 2013-08-02
Hey bcariddi! :)

This document might help you: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

//Egonosaur

---

