---
title: "ASUS WL-138G V2 Lucid Lynx Wireless problem! HARD TO SOLVE!"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by Green Moon on 2010-12-20
[COLOR=Black]Alright, I'm TOTALLY new to Ubuntu (it's my second day right now) and I have a problem that I cannot find a solution to ANYWHERE in the internet! I've researched like crazy, but haven't been able to find a suitable solution to fixing the ASUS WL-138G V2 's wireless to work on Lucid Lynx ( Ubuntu 10.04 ). I got the driver; got Ndiswrapper. Managed to install Ndiswrapper, and installed my card's driver using it. It shows "Hardware found: Yes" but it does not find ANY access point!

Can someone please help me out here?
Note: It is NOT possible for me to use ANY internet on Ubuntu whatsover - I have no temporary internet connection other than my only wireless connection. So, I have to use it on Windows 7, which I have installed with Lucid Lynx.

Machine Brand and Model

PC

Wireless Brand, Model and Wireless Chipset:

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


Something -
id=750 name="/usr/bin/evince-previewer"
[   10.846123] type=1505 audit(1292850482.439:11):  operation="profile_load" pid=750 name="/usr/bin/evince-thumbnailer"
[   10.867720] zc3xx: probe sensor -> 000a
[   10.867752] zc3xx: Find Sensor PB0330. Chip revision 0
[   10.871811] gspca: probe ok
[   10.871849] usbcore: registered new interface driver zc3xx
[   10.871854] zc3xx: registered
[   11.110079] r8169: eth0: link down
[   11.110390] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.164099] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   11.196845] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   11.199218] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.199224] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.199226] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   11.232568] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   11.242151] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   11.245357] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   11.245362] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.245365] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website
_________________________

Network configuration:


*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:c0:d9:0c:50
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:d000(size=256) memory:fb220000-fb220fff memory:fb200000-fb21ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:04:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:20 memory:fb100000-fb101fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1d:60:7e:85:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

____________

Scan for networks:


wlan0     Failed to read scan data : Network is down


OS version:



Ubuntu 10.04.1 LTS


kernel version:

2.6.32-24-generic i686

Restarting the network:

* Reconfiguring network interfaces...                                   [ OK ] 


[/COLOR]

---

### Post by Green Moon on 2010-12-20
Any help?

---

### Post by chili555 on 2010-12-20
I wish all of my problems were this easy to solve! The answer is right in the message logs!> b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not foundAttached to this reply is a zip file. Transfer it to your Ubuntu machine and drag and drop it to the desktop. Right-click it and select 'Extract Here.' Open a terminal and do:```
sudo mkdir /lib/firmware/b43
cd Desktop
sudo cp ucode5.fw /lib/firmware/b43
sudo reboot
```Is your wireless working now?

---

### Post by Green Moon on 2010-12-20
No luck. :( It's still the same as ever. :(

Still need help.

---

### Post by chili555 on 2010-12-20
Please post:```
dmesg | grep b43
ls -al /lib/firmware/b43
```Thanks.

---

### Post by Green Moon on 2010-12-20
The first code gave this:


[    2.443593] b43-pci-bridge 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   10.231162] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   10.349932] Registered led device: b43-phy0::tx
[   10.349950] Registered led device: b43-phy0::rx
[   10.349967] Registered led device: b43-phy0::assoc
[   10.349984] Registered led device: b43-phy0::radio
[   11.180058] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   11.226247] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   11.228320] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   11.231384] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   11.234775] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   11.234781] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.234784] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   11.264258] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   11.266964] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   11.327554] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   11.330173] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   11.333805] b43-phy0 ERROR: Firmware file "b43/b0g0initvals5.fw" not found
[   11.333810] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   11.333813] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.


Second one gave this:


total 32
drwxr-xr-x  2 root root  4096 2010-12-20 19:48 .
drwxr-xr-x 50 root root  4096 2010-12-20 20:08 ..
-rwxr-xr-x  1 root root 22264 2010-12-20 20:10 ucode5.fw

---

### Post by Green Moon on 2010-12-20
So what should I do next?

---

### Post by chili555 on 2010-12-20
Here is another file. Use the same process.

---

### Post by Green Moon on 2010-12-20
Sorry I'm asking you this but, how do I load them all at once? There are many firmware files! Do I just do them one at a time?

Thanks for your help so far btw.. I really appreciate it :)

---

### Post by chili555 on 2010-12-20
No problem; glad to help. You should have a folder on your desktop called b43 after you extracted the second zip file. Open a terminal and do:```
cd Desktop/b43
sudo cp * /lib/firmware/b43
```The wildcard * means, in this context, to copy everything in the folder. Post back if you get stuck.

---

### Post by Green Moon on 2010-12-20
OH MY GOD DUDE I LOVE YOU! It's working! THANKS A LOT FOR YOUR HELP! Just made me realize how small this problem was. :P It wasn't that big at all! And you made me realize that! THANK YOU SOO MUCH! :D :D

---

### Post by chili555 on 2010-12-20
Woo hoo!!! I am very glad it's working. Enjoy Ubuntu and post back if we can help you further.

---

### Post by ArkadioG on 2013-01-08
This worked also on Mint 14 Nadia, I had problem with this Asus card.

Thanks alot!

---

