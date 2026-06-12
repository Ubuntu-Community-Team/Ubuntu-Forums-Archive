---
title: "Intel PRO Wireless 4965 AG / AGN, Lenovo T61"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by Demosthenes64 on 2013-04-22
If this is in the wrong section, please let me know. I had windows 7, on my Lenovo T61, but that became pretty long in the tooth so I decided to go to Ubuntu, had 12.10 and JUST upgraded to 13.04. I've fiddled around with terminal, installed a couple of programs using it, but I'm still an "absolute beginner," so I would appreciate some help installing drivers that are missing, such as the webcam and bluetooth. I've heard of NDISWrapper, but I've read that you need to run sudo commands and have been warned to be very careful when running sudo commands if you don't know what it does/means. So if anybody could give me a step-by-step that would be awesome.

---

### Post by deadflowr on 2013-04-22
To give us an idea of what you have please run these two commands and post the output.
```
lspci
```
and```
lsusb
```

When posting the output, please use the code tags (It's the # symbol in the reply box)

These two commands should give us a rough idea of what you have.

---

### Post by sudodus on 2013-04-22
The device drivers are managed in different ways in linux compared to Windows. They come with the kernel, and are expected to work without any installation. But there are exceptions. Some hardware have no linux drivers. Some hardware have proprietary linux drivers, that you download and install, particularly graphics chips/cards, wifi chips/dongles/cards, printers. I think ndiswrapper is used only for wifi devices (but I may be wrong), but I know that it is difficult to get good performance with ndiswrapper an a Windows driver.

Instead, buy hardware that is known to work with linux :-) You can get help here at the Ubuntu Forums. I think you are pretty lucky with the Lenovo T61, it should work well with Ubuntu and the other flavours Lubuntu, Xubuntu, Kubuntu ...

---

### Post by Demosthenes64 on 2013-04-22
lspci```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

```

lsusb```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by mörgæs on 2013-04-22
Hi, welcome to the fora. 

Your post has been moved to Wireless and Networking and renamed. Please take a look around and see if you find advice here for your network card.

Ndiswrapper should be used only as a last resort.

---

### Post by chili555 on 2013-04-22
I have the exact same wireless card in a Lenovo T60. The driver is built in. It is called iwl4965. It is probably already loaded. Please check:```
lsmod | grep iwl
```The pipe symbol | is located on the right side of my US keyboard on the same key with \.

If you find it *is* loaded, the next thing to check is the wireless switch or key combination; Fn+F5 on my T60. Many countries, including the USA, require a physical slide switch in addition to the key combination. Check:```
rfkill list all
```Please see here: [http://forums.lenovo.com/t5/image/serverpage/image-id/165i90E5591738AB0633/image-size/medium?v=mpbl-1&px=-1](http://forums.lenovo.com/t5/image/serverpage/image-id/165i90E5591738AB0633/image-size/medium?v=mpbl-1&px=-1)

---

