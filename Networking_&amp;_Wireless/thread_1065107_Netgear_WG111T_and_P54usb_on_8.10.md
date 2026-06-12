---
title: "Netgear WG111T and P54usb on 8.10"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by ranpha on 2009-02-09
Hi there,

I tried to get my netgear wg111t working again under ubuntu.Normally i will use nidswrapper but i came across the p54 driver in the kernel.

I also found this [http://www.linuxforums.org/forum/wireless-internet/135813-opensuse-wusb54gv2-wireless-adapter-woes.html](http://www.linuxforums.org/forum/wireless-internet/135813-opensuse-wusb54gv2-wireless-adapter-woes.html)

I follow the first steps and when i did 

lsusb I got this

Bus 007 Device 002: ID 1385:4251 Netgear, Inc WG111T (no firmware)

When i did "lsmod" however there was no p54usb module loaded. I found this strange so i forced it loaded in /etc/modules. Still no message in dmesg that the device was working. So i looked for the firmware and i noticed that the firmware was already their in /lib/firmware.
So that kinda make me get stuck and here to ask for some hints how to get the netgear wg111t working with the p54usb driver.

---

### Post by alexxroche on 2010-02-19
I managed to get the Netgear WG111T (I'm normally a fan of Tea but not in this case!)

I downloaded [ftp://downloads.netgear.com/files/wg111t_2_1_setup.exe](ftp://downloads.netgear.com/files/wg111t_2_1_setup.exe) and ran it using wine (just to extract the drivers.)
I then followed the instructions on [https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T)

(install ndisgtk using synaptic or apt-get)
and then directed 
System -> Administration -> Windows Wireless Drivers
to the divers (well the .inf file)  ~/.wine/drive_c/Program\ Files/NETGEAR/WG111T/Driver/netwg11t.inf

... and it worked. 

alexx

p.s. I tried with the 1.2 version of the driver, but that didn't work for me. If NETGEAR are reading this, please leave an unbundled version of your dirver so I don't have to install other netgear things just to get to the dirvers, (or better yet contribute a Linux driver for your hardware, so that paying customers are not forced into using anything less than linux.)

p.p.s Does not work with airmon-ng

---

