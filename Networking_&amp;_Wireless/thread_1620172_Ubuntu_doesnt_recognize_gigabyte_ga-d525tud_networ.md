---
title: "Ubuntu doesnt recognize gigabyte ga-d525tud network card"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by pvi on 2010-11-12
Just bought me a GIGABYTE GA-D525TUD (with Realtek RTL8111E network chip) motherboard for making a home NAS. 
 
I downloaded and installed Ubuntu 10.10 server, but the network isnt recognized during install.
 
After the install I downloaded the realtek linux drivers (from [http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false)) and tried to compile and install them (with the instructions from the readme). This seemed to go ok, but I still dont have a network (kinda important for a NAS). I stopped at the 1.b part in the readme, because I could not find the /etc/resolv.conf.
 
I dont know too much about linux and dont know what to do now.
 
Can anyone help me?
 
Regards,
 
Paul.

---

### Post by chili555 on 2010-11-12
I thought the RTL8111E was supported by a driver module that's already built in to the kernel. I'd like to know a few more details about your card. Please open a terminal and do:```
lspci -nn
```Post the line describing your Realtek and we'll have a better idea how to proceed.

---

### Post by pvi on 2010-11-13
This is the output for lspci -nn:
```
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a000] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a001] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
02:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)

```
 
Cant really find the Realtek line.

---

### Post by chili555 on 2010-11-13
I don't either, nor any other network device. Let's also see:```
lsusb
sudo lshw -C network
```Thanks.

---

### Post by pvi on 2010-11-13
Very strange. To eliminate that it was a hardware failure I installed Windows 7. The network card was working correct there (after installing the drivers from the GIGABYTE CD). After that installed Ubuntu again, and now it DID detect the network card. Dont know why, but anyway, problem is solved.
 
Thanks for reacting.
 
Paul.

---

### Post by uncaspi on 2010-11-13
Please mark the thread as solved:)

---

