---
title: "Wireless Card Unidentified ??!!!"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by iceflow on 2011-05-15
[SIZE=3]Wireless Issue On Ubuntu 11.04

I recently Replaced Windows XP by Ubuntu 11.04 on a Dell Inspiron 5100 ( Mini PCI Network Card) :D Everything looked great till I found that I can't connect through wireless but only on Ethernet.
I checked many forums and found out that Running windows Drivers Under Ubuntu is possible using Ndiswrapper, I followed Every step from Extracting The .exe file on my dektop till executing the .inf and .sys file, but here is the weird thing, on my windows wireless drivers, it says that the driver is installed, but still no INTERNET access through wireless, The Wireless icons are blank and say "Device not Ready, Firmware missing", I cant get access to Device manager tool which do not exist on my Applications manu[/SIZE][SIZE=3]! :confused::confused::confused:[/SIZE][SIZE=3]       Am ever gonna find out why!
Here Is the link of the web page I used as a reference and some info you might need:

[http://www.techmetica.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/](http://www.techmetica.com/howto/how-to-install-windows-wireless-network-device-drivers-in-ubuntu/)
~lspci

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
~nfconfig

eth0      Link encap:Ethernet  HWaddr 00:0d:56:af:5c:e1  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feaf:5ce1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15380 errors:110 dropped:26 overruns:0 frame:0
          TX packets:12846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18159902 (18.1 MB)  TX bytes:1889478 (1.8 MB)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12164 (12.1 KB)  TX bytes:12164 (12.1 KB)

[/SIZE]

---

### Post by uncaspi on 2011-05-15
Try to go to Broadcom homepage and download the latest STA driver and unpack it and follow the instruction on the README file.

---

### Post by nm_geo on 2011-05-15
Do this in terminal
```
 
lspci -vnn | grep 14e4
```Paste the results here.

Go to Synaptic and read and check the properties on this package.

 firmware-b43legacy-installer

I believe you will also need the

b43-fwcutter

---

### Post by iceflow on 2011-05-16
> **nm_geo said:**
> Do this in terminal
```
 
lspci -vnn | grep 14e4
```Paste the results here.

Go to Synaptic and read and check the properties on this package.

 firmware-b43legacy-installer

I believe you will also need the

b43-fwcutter

[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]
    Subsystem: Broadcom Corporation Device [14e4:4d64]
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by garvinrick4 on 2011-05-16
open synaptics and type in bcm so users can see what you have installed.
like this: I have highlighted your drivers. I do not use broadcom cards but
lots of others do and can see exactly what you need to get running.
bcm4306 rev (03) is what you have: and you need the b43-fwcutter package:

---

### Post by iceflow on 2011-05-16
> **uncaspi said:**
> Try to go to Broadcom homepage and download the latest STA driver and unpack it and follow the instruction on the README file.

Hi,
I downloaded the latest STA on Broadcom, And following the readme instructions, I couldnt Build the module, every command returned nagatively:

~$ apt-get install build-essential linux-headers-generic
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Beside, When I try To install packages on Synaptic, I get: 

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1

Im Lost :confused: but im not giving up now :)

---

### Post by garvinrick4 on 2011-05-16
Edit: Look at your synaptics type bcm and highlight to see what you need
for your card.

windows key and A 
type in Additional drivers click on
enable it if needs be.

---

### Post by iceflow on 2011-05-16
> **nm_geo said:**
> Do this in terminal
```
 
lspci -vnn | grep 14e4
```Paste the results here.

Go to Synaptic and read and check the properties on this package.

 firmware-b43legacy-installer

I believe you will also need the

b43-fwcutter

Hi, 
I looked for firmware-b43legacy-installer on Synaptic, I found it but Errors occured during the installation, and a request to report a system problem popped up, is that means my OS is corrupted or something?

E: firmware-b43-lpphy-installer: subprocess installed post-installation script returned error exit status 1
E: firmware-b43legacy-installer: subprocess installed post-installation script returned error exit status 1

---

### Post by iceflow on 2011-05-17
> **garvinrick4 said:**
> Edit: Look at your synaptics type bcm and highlight to see what you need
for your card.

windows key and A 
type in Additional drivers click on
enable it if needs be.


Thanks A LOt Guys, Wireless Connection Established  :)
Thanks To Uncaspi ,GarvinRick 4 And nm_Geo, Ure the best guys

---

### Post by garvinrick4 on 2011-05-17
Looks like you had a day long battle I am glad to see you stuck it out. It is not like that
in Linux, it is those broadcom wifi cards that are tough for new users to get going, not
to tough once you do it once. Lots of users here to help, stick around these forums and
read threads and posts. And google, google and more google helps a bit at times when trying
to learn something new.

---

