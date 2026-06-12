---
title: "D-Link DWL-G520+ no longer detected on Ubuntu 9.10"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by smallbear on 2009-11-30
My D-Link DWL-G520+ card is not detected by Ubuntu 9.10, despite being detected automatically on Ubuntu 7.04, which I have been using previously until now.

I have not tested with 9.04 or prior.

ifconfig does not show the interface...

user@ubuntuserver:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:46:99:eb:dd  
          inet6 addr: fe80::213:46ff:fe99:ebdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1836 (1.8 KB)
          Interrupt:10 Base address:0x1080 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


lspci shows the card.  It's the last-but-one line.  Incidentally the D-Link DFE-550TX Ethernet is detected and works on installation.

user@ubuntuserver:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0f.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 15)
00:10.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (rev 3a)


There is nothing about the Wireless card in 'dmesg'.  It shows the Ethernet card only.

uname -mr
2.6.31-14 Generic i386

sudo /etc/init.d/networking restart

* Reconfiguring network interfaces
Ignoring unkown interface eth0=eth0.

---

### Post by chili555 on 2009-11-30
Please see here: [http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303)

I tested this by compiling the driver and patch without errors but I do not have the device to test it with.

---

### Post by smallbear on 2009-11-30
It didn't work for me, unfortunately.  Results were unchanged and nothing listed in ifconfig.  Thanks anyway.

Does this mean that at some time in the past, the driver (which previously was included) has been dropped form Ubuntu?

---

### Post by chili555 on 2009-11-30
> Results were unchanged and nothing listed in ifconfig.Did *acx.ko* get insmodded successfully? If so, please run:```
dmesg | grep acx
```Please post the result.> Does this mean that at some time in the past, the driver (which previously was included) has been dropped form Ubuntu? Not from Ubuntu, but from the 2.6.30-x, or so kernels, yes.

---

### Post by DaveBG on 2009-12-12
I have the same issue. Does anyone know how can this be enabled in Ubuntu 9 so that i can connect to internet?

---

### Post by chili555 on 2009-12-12
See post #1 here: [http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303)
Follow the 'make' step with this:```
sudo make -C /lib/modules/`uname -r`/build M=`pwd` modules_install
```

There are a few other steps. First:```
sudo cp /lib/firmware/acx/1.9.8.b/tiacx100 /lib/firmware
sudo cp /lib/firmware/acx/1.9.8.b/tiacx100r0D /lib/firmware
```Next, let's load the module permanently:```
sudo gedit /etc/rc.local
```Add a new line, just above 'exit 0.'```
cd ~/acx/acx-20080210 && insmod acx.ko
```Use kate or nano or vim, if you don't have gedit. Upon reboot, you should have a new wireless interface, *wlan0*.

---

### Post by DaveBG on 2009-12-18
Hi. Thank you for that. I did it and upon reboot i still do not have wireless. It only shows wired.

I had some problems getting "patch" but i downloaded it on windows and installed it manually :)

So still does not detect the wireless card...

---

### Post by changingstate on 2009-12-18
I managed to get the Ax revision of this card operating with ndiswrapper in Karmic last night. Apologies if this is old ground, but I just grabbed the driver here :

[http://www.dlink.co.uk/cs/Satellite?c=TechSupport_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319532809&p=1197318962293&packedargs=locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper]("http://www.dlink.co.uk/cs/Satellite?c=TechSupport_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319532809&p=1197318962293&packedargs=locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper")

Extracted it to a folder, pointed ndiswrapper at <folder>/driver/WinXP/GPLUS.inf and I was away.

My network is running WEP, I've not tested with WPA.

---

### Post by DaveBG on 2009-12-18
Erm i am running ubuntu. This is for windows...

---

### Post by chili555 on 2009-12-18
> **DaveBG said:**
> Erm i am running ubuntu. This is for windows...He is suggesting you use the Windows driver with ndiswrapper. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by DaveBG on 2009-12-24
It works!

Thank you so much!

I have to run every startup:
  sudo depmod -a
  sudo modprobe ndiswrapper

but i will add these to startup commands not to bother anymore :)

10x again!

---

### Post by baram204 on 2010-02-25
Hi i have G520+

I found solution.

From Internet, Download tnet1130 driver.

and Using ndiswraper. install tnet 1130 driver into your Ubuntu machine.

It work!!

Driver from the d-link.. & madwifi ... ath5, ath9 

won't work.. i tried about hundred time..

compile and change over and over.. it won't work..

use Tnet 1130 driver!!

---

### Post by alfh on 2010-05-10
> **changingstate said:**
> I managed to get the Ax revision of this card operating with ndiswrapper in Karmic last night. Apologies if this is old ground, but I just grabbed the driver here :

[http://www.dlink.co.uk/cs/Satellite?c=TechSupport_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319532809&p=1197318962293&packedargs=locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper]("http://www.dlink.co.uk/cs/Satellite?c=TechSupport_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319532809&p=1197318962293&packedargs=locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper")

Extracted it to a folder, pointed ndiswrapper at <folder>/driver/WinXP/GPLUS.inf and I was away.

My network is running WEP, I've not tested with WPA.

This link and ndiswrapper seems to be steps in the right direction. At least ndiswrapper found the hardware after installing this driver, but I still haven't figured out how to actually connect to the wireless network.

---

### Post by alfh on 2010-06-15
So finally got it working on 10.04 and figured out why I had problems: I was prevously trying to compile an acx driver and during this process it was recommended to stop using nm-manager. So I disabled it from the system > settings > startup programs and forgot about it... Enabled it again and now it's working!

So my steps were:

1. Go to this link and get the ax revision of the driver: 
[http://www.dlink.co.uk/cs/Satellite?c=TechSupport_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319532809&p=1197318962293&packedargs=locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper]("http://www.dlink.co.uk/cs/Satellite?c=TechSupport_C&childpagename=DLinkEurope-GB%2FDLTechProduct&cid=1197319532809&p=1197318962293&packedargs=locale%3D1195806691854&pagename=DLinkEurope-GB%2FDLWrapper")

2. Follow this guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") (The guide's 2.2 doesn't give instructions for 10.04 yet, but I found ndiswrapper in synaptic and took it from there)

I don't know yet if encryption works, for now I'm just happy there is internet. Woooo!

Edit: Didn't manage to connect when network was invisible, but wpa security is working.

---

