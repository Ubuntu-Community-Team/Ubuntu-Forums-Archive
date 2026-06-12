---
title: "Re: wireless connection very unstable"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by se7ensense7en on 2010-11-02
My problem is a little bit strange!

I have installed Ubuntu 10.10 for 4 times: Three inside Windows and One along with Windows 7. All of them resulted in very silly and frustrating internet connection which cannot be found on Windows!

There was an icon indicating that the connection from the computer to my home router was successfully established, but it turned to be disconnected as soon as I entered a webpage or tried to install/update/upgrade software. Then Ubuntu cannot connect to the router any more. I had to remove the wireless adapter from the USB port and plugged it in again after a few minutes to have the connection "re-established". If I tried to install/update/upgrade a new software, it lost again!

Here is some information about my devices that may be helpful:

[LIST=1]
[*]ROUTER: D-LINK DIR 615 or BUFFALO G54
[*]ADAPTER: D-LINK DWA 140 (Hardware Version: B1, Firmware Version: 1.30)
[*]MAINBOARD: ASUS P7H55D-M PRO
[*]CPU: INTEL CORE I3 530
[/LIST]
It will always be my happiness to have any information/solution/suggestion from you!

---

### Post by pytheas22 on 2010-11-02
Do you have Ubuntu installed inside a virtual machine, using a program like VirtualBox or VMware? Or do you have a dual-boot system that will allow you to boot into either Ubuntu or Windows?

With a virtual machine, you shouldn't need to use a USB wireless adapter for Ubuntu. You can share the Internet connection with the host operating system, which is much easier. (You could make the guest machine use the USB adapter if you wanted, but in most cases there would be no reason to do so.)

It would also be helpful to see the outputs from you of:
Code:
```

lspci -nn
lsusb
lshw -C Network
uname -a
```

---

