---
title: "wireless problem"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by mjzanga on 2010-03-24
Just installed Ubuntu 9.10 on my laptop. Everything works great except for the wireless which refuses to connect. I can enter all the information about my wireless network but it still does not work. I am completely new to Ubuntu and Linux in general so I have no idea where to start. any help would be greatly appreciated.

---

### Post by paulrogers on 2010-03-24
Applications --> Accessories --> terminal

Type in:

sudo iwlist scan

then

iwconfig

post the results back here

Thats all I can do, with them results somebody else may be able to begin helping you

---

### Post by 2hot6ft2 on 2010-03-24
Open a terminal
Applications > Accessories > Terminal
and run
If an internal wifi adapter
```
lspci
```
That's LSPCI in lower case, and post the results.

If a usb wifi adapter
```
lsusb
```
That's LSUSB in lower case, and post the results.

So we can see what wireless adapter you have.

---

### Post by mjzanga on 2010-03-24
michael@jim-laptop:~$ sudo iwlist scan

lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


pan0      Interface doesn't support scanning.


wmaster0  Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Network is down



michael@jim-laptop:~$ iwconfig

lo        no wireless extensions.


eth0      no wireless extensions.


pan0      no wireless extensions.


wmaster0  no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:""
  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
 
           Tx-Power=0 dBm
 
           Retry  long limit:7   RTS thr:off   Fragment thr:off

            Power Management:off

            Link Quality:0  Signal level:0  Noise level:0

            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

even though ive put all the information in for the wireless network it doesn't associate itself with that network. or so it seems anyway

---

### Post by mjzanga on 2010-03-24
sorry bout the emoticons

---

### Post by 2hot6ft2 on 2010-03-24
> **mjzanga said:**
> sorry bout the emoticons
No problem. Put the results in a code box by highlighting it and clicking on the # at the top of the reply box. Not the ones you already gave but these.

That's what I was expecting from the iwlist commands we need to find out what adapter you have with either the lspci or lsusb commands I gave.

---

### Post by mjzanga on 2010-03-24
michael@jim-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)


if it helps at all i used to have windows XP on the laptop

---

### Post by mjzanga on 2010-03-24
> **2hot6ft2 said:**
> No problem. Put the results in a code box by highlighting it and clicking on the # at the top of the reply box. Not the ones you already gave but these.

sorry didn't see that soon enough.

---

### Post by 2hot6ft2 on 2010-03-24
> **mjzanga said:**
> 
0c:00.0 Network controller: **Broadcom Corporation BCM4311** 802.11b/g WLAN (**rev 01**)

That's your wifi adapter right there. And here's the guide to getting it working:
[[SOLVED] The Definitive 9.10 Broadcom Solution Guide]("http://ubuntuforums.org/showthread.php?t=1368699")

No problem

---

### Post by mjzanga on 2010-03-24
alright I'l try it out. thanks for the help I'll let you know how it works out

---

### Post by 2hot6ft2 on 2010-03-24
> **mjzanga said:**
> alright I'l try it out. thanks for the help I'll let you know how it works out
I'm sure you'll get it fixed up. You're welcome and enjoy.

---

### Post by mjzanga on 2010-03-24
well after installing 247 updates and activating the driver it works just fine. thanks a ton!

---

