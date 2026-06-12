---
title: "D-Link  DWA-110 Wireless adapter"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by ercanizzet on 2009-05-13
Hi all,
I am new user of Linux and Linux Ubuntu. I installed Ubuntu 9.04 today. I have wireless network at home and my desktop has D-Link DWA-110 Wireless adapter. As you guess i could not find the Linux driver of this adapter. Could ony one help me to find related driver or write me in detailed how to Linux detect this adapter? Please do not forget i am realy beginer for Linux.

---

### Post by uupreti on 2009-05-13
Go to terminal. By pressing ALT-F2 and enter gnome-terminal and hit enter. Then give the output of following commands.
[B]1. lshw -C network
2. ifconfig
3. iwconfig
4. iwlist scan[/B]

---

### Post by bkratz on 2009-05-13
You may also wish to look here

 [http://ubuntuforums.org/showthread.php?t=891363](http://ubuntuforums.org/showthread.php?t=891363)

---

### Post by ercanizzet on 2009-05-14
Thank you very much. I will try ...

---

### Post by Truthseekernz on 2009-08-04
My DWA-110 USB Wi-fi adaptor worked on Ubuntu 9.04 right out of the box up to kernel 2.6.27-14. Kernels after that see the device stone dead. I haven't had time to work out why. I just keep booting Ubuntu in kernel 2.6.27-14....and I'm online. I try each new kernel as it comes out, but as of 2.6.28-15, the DWA-110 is still stone dead....so I keep using 27-14.

---

### Post by keplerspeed on 2009-08-04
It appears that this adapter requires ndiswrapper and the windows driver.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

In that case, see here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Truthseekernz on 2009-08-28
> **keplerspeed said:**
> It appears that this adapter requires ndiswrapper and the windows driver.


I have it working fine on 2.6.27-14 (and several Ubuntu kernels prior) - out of the box, no Windows drivers. 

But on the several kernels since that kernel (current one is 2.6.28-15), the device does not work. 

So I keep booting 2.6.27-14.....no ndiswrapper. No Windows drivers.  Ubuntu Desktop 9.04.

---

