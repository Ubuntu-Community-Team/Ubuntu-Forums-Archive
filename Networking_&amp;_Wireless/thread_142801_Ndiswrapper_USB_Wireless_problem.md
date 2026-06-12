---
title: "Ndiswrapper USB Wireless problem"
date: 2006-03-11
forum: Networking &amp; Wireless
---

### Post by jingo811 on 2006-03-11
I've been wrestling with some Ndiswrapper complications for 1 whole month now.
Trying to solve my USB pentype Wireless in Ubuntu.
And also the so called chipset List link in the Wiki I found this about my wireless:
> 
Card: Asus WL-161, 11mbps

* Chipset: Sis162u USB
* usbid: 2821:0161
* Driver: CDRom, WinXP driver. (sis162u.inf, original at [www.sys.com](www.sys.com))
* Other: Use "ndiswrapper -d 2821:0161 sis162u"... to get Hardware present. It works perfect on 11 mbps!
With those fact you might be able to see what I'm doing wrong.
OK, so these are the procedures that I did but didn't make the Internet work.

> mike@Compaq:~/Linux$ **cd drivers**
mike@Compaq:~/Linux/drivers$ **ls**
sis162u.inf  sis162u.sys
mike@Compaq:~/Linux/drivers$ **sudo ndiswrapper -i sis162u.inf**
Password:
Installing sis162u
mike@Compaq:~/Linux/drivers$ **sudo ndiswrapper -l**
Installed ndis drivers:
sis162u driver present
mike@Compaq:~/Linux/drivers$ **sudo modprobe ndiswrapper**
mike@Compaq:~/Linux/drivers$ **sudo depmod -a**
mike@Compaq:~/Linux/drivers$ **sudo modprobe ndiswrapper**
mike@Compaq:~/Linux/drivers$** ifconfig**
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1033987 (1009.7 KiB)  TX bytes:1033987 (1009.7 KiB)

When checking for the Asus USB Wireless I can't find the name **wlan0** anywhere:
> mike@Compaq:~$ **lsusb**
Bus 001 Device 005: ID 2821:0161
Bus 001 Device 004: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 4 50L Optical Mouse
Bus 001 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 001 Device 001: ID 0000:0000

What am I doing wrong?  I've spent almost 2 months reading up in Wiki on all the material of Ndis and I don't want to go over the whole experience of trying to uninstall Ndiswrapper and compiling the newest version again.  That attempt occupied one whole month without solving anything and worst there wasn't any support for that.
So with that in mind my ifconfig knowledge is minimal at this point :-)

---

