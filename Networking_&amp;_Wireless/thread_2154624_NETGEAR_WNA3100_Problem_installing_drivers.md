---
title: "NETGEAR WNA3100 Problem installing drivers"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by knagieknagger on 2013-06-15
Hello,

I installed Ubuntu studio 13.04 2 days ago because i wanted to record videos for Minecraft.
So i installed Minecraft with some trouble but it works now :smile:.

only problem is i cant get my NETGEAR WNA3100 to work with ubuntu studio

(i am currently connected with a network cable running through the complete house to my router)

i searched on the forums and tryed several different solutions but none of them worked :sad:

maybe someone can give me a fresh start! 

i ran this command:

lspci | grep Wireless

and got nothing on screen.

System exists of:

320GB HDD with Ubuntu 13.04 64-Bit and an 500GB HDD with windows 7 Pro 64-Bit


if you need more info please say so and i will try to provide as much as possible!

Niels

---

### Post by chili555 on 2013-06-15
> lspci | grep WirelessPlease try:```
lsusb
```It is a USB device and not a PCI, correct? [http://www.netgear.com/home/products/wireless-adapters/work-and-play/WNA3100.aspx#](http://www.netgear.com/home/products/wireless-adapters/work-and-play/WNA3100.aspx#)

When you find the ID, search this forum for the details and find 163,000 posts about how to get it going. It may look something like this:>  [COLOR="#FF0000"]0846:9020[/COLOR] NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]As there are several versions of this device, be sure to match the usb.id I've highlighted.

---

### Post by knagieknagger on 2013-06-15
so i followed your advise and searched on the forums and used the USB command instead of the PCI command and here is the result ((because it didnt worked) for your information this is the first time i did the commands, and i installed ndiswrapper yesterday)

I did:

```
lsusb
```

I get this:

```
niels@ubuntu:~$ lsusb
Bus 004 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 007 Device 002: ID 0582:012a Roland Corp. 
Bus 008 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 008 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 009 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
niels@ubuntu:~$ 
```

then i followed the instructions from this thread:
[ubuntuforums.org/showthread.php?t=1946875&highlight=NetGear%2C+WNA3100(v1)+Wireless-N+300+]("http://ubuntuforums.org/showthread.php?t=1946875&highlight=NetGear%2C+WNA3100(v1)+Wireless-N+300+")[Broadcom+BCM43231]

So i did this:

```
sudo ndiswrapper -e bcmwlhigh5
```

I get this:
```
niels@ubuntu:~$ sudo ndiswrapper -e bcmwlhigh5
[sudo] password for niels: 
couldn't delete /etc/ndiswrapper/bcmwlhigh5: No such file or directory
niels@ubuntu:~$ 
```

Then i did this:

```
sudo rm -rf /etc/ndiswrapper/*
```

I get this:
```
niels@ubuntu:~$ sudo rm -rf /etc/ndiswrapper/*
[sudo] password for niels: 
niels@ubuntu:~$ 
```

Then i did this
I downloaded the file attached and put it on my desktop like said in the post
```
sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf
```

Then i get this: (this is weird because with the previuos command we deleted it right?)

```
niels@ubuntu:~$ sudo ndiswrapper -i Desktop/wna3100-drivers/bcmwlhigh5.inf
[sudo] password for niels: 
driver bcmwlhigh5 is already installed
niels@ubuntu:~$ 
```

Well i continued because it says it is installed

so i did this:
```
ndiswrapper -l
```

and got this: (maybe because of the 64 and 32 bit drivers?)
```
niels@ubuntu:~$ ndiswrapper -l
bcmwlhigh5 : invalid driver!
niels@ubuntu:~$ 
```

I got a 64 bit version version of Ubuntu Studio 13.04 so maybe these drivers are for 32bit?

maybe you can help me because as far as i know i didnt do something wrong (but i am new though so i could have done something stupid/wrong without knowing)

---

### Post by chili555 on 2013-06-15
Let's see what the message logs have to say:```
dmesg | grep ndis
```> maybe because of the 64 and 32 bit drivers?Probably; let's see what the logs say.

---

