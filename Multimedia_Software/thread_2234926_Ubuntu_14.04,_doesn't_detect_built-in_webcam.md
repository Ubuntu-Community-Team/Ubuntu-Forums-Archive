---
title: "Ubuntu 14.04, doesn't detect built-in webcam"
date: 2014-07-17
forum: Multimedia Software
---

### Post by ida2 on 2014-07-17
Hi! I am running ubuntu 14.04 on an MSI GS70 laptop. The system doesn't detect the built in webcam. Cheese says that no device is found. I am new to Ubuntu, I have looked on this forum but I couldn't find a solution. Below is the output I get when I type lsusb, lspciand lsmod |grep video. I will be very thankful for any help! :-)

user@user-GS70-2OD:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 010: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 009: ID 1770:ff00  
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@user-GS70-2OD:~$ 

user@user-GS70-2OD:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev ff)
04:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)
05:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)
user@user-GS70-2OD:~$ 



user@user-GS70-2OD:~$ lsmod | grep video
video                  19476  1 i915

---

### Post by ibjsb4 on 2014-07-18
Wow, thats one kick butt machine.

I use cheese, maybe that will work for you.

[https://help.ubuntu.com/community/Webcam#Testing_Your_Webcam_Using_Cheese](https://help.ubuntu.com/community/Webcam#Testing_Your_Webcam_Using_Cheese)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=webcam&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=webcam&sa=Search&cof=FORID:9)

---

### Post by humberto2 on 2015-04-17
I know that a long time passed since you posted.


  with lspci get:

  00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
  
The solution was to activate the webcam with the keys: fn + CAM  in my case f10.

  I hope this helps. Regards.

---

