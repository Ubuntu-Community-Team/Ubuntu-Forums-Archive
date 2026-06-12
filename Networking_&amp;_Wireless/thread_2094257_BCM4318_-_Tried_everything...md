---
title: "BCM4318 - Tried everything.."
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by DJAlo on 2012-12-13
Hi everyone,

I have a problem on my Acer TravelMate 2400 with Ubuntu 12.10 on the BCM 4318 wireles card, i tried every guide, installed STA drivers, b43 drivers ecc, but still no progress in getting wifi working, the b44 driver ( lan ) is working good, and I'm now writhing from my Acer attached to my LAN network, but i also want to use the wifi around my house.
What can I do ? I'm confused, I don't know what to do..

---

### Post by chili555 on 2012-12-13
Let's identify exactly which card you have. Please run and post:```
lspci -nn | grep 0280
rfkill list all
```Thanks.

---

### Post by DJAlo on 2012-12-13
Hi, thanks for Your reply, here You have:
> 
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


Also tried to sudo modprobe b43 and nothing happens... every reboot I do sudo modprobe b44 to activate wired, i can load it to start automatically, but doesn't matter, i want to use only the wifi

---

### Post by chili555 on 2012-12-13
Please do:```
sudo su
apt-get remove --purge bcmwl-kernel-source
echo b43 >> /etc/modules
exit
```Reboot and run and post:```
lsmod
rfkill list all
```Thanks.

---

### Post by DJAlo on 2012-12-13
Here You are:

It's not readable in quote, here You have the .txt on my server: [www.djalo.bplaced.net/linux.txt](www.djalo.bplaced.net/linux.txt) Just open and read :)

Thanks :)

---

### Post by chili555 on 2012-12-13
And how about the rest?```
rfkill list all
```Any change in your wireless?

---

### Post by DJAlo on 2012-12-13
> 
rfkill list all


Nothing happens, no WiFi all the time, but I have a popup with wifi signal bar and Information that I'm online, but Networking is online and any wifi.

---

### Post by chili555 on 2012-12-13
> but Networking is online and any wifi.I'm sorry, I don't understand. Please post:```
dmesg | grep wlan
nm-tool
```Thanks.

---

### Post by DJAlo on 2012-12-13
> **chili555 said:**
> I'm sorry, I don't understand. Please post:```
dmesg | grep wlan
nm-tool
```Thanks.

> 
alan@alan-TravelMate-2400:~$ dmesg | grep wlan
alan@alan-TravelMate-2400:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        00:0F:B0:7E:79:C6

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


P.S I wasn't logged to my LAN network

Thanks

---

### Post by chili555 on 2012-12-13
> alan@alan-TravelMate-2400:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
Type: Wired
Driver: b44
State: unavailable
Default: no
HW Address: 00:0F:B0:7E:79:C6

Capabilities:
Carrier Detect: yes

Wired Properties
Carrier: off We see no wireless interface at all. This is getting most interesting! Let's see:```
iwconfig
cat /etc/network/interfaces
```

---

### Post by DJAlo on 2012-12-13
> 
alan@alan-TravelMate-2400:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

alan@alan-TravelMate-2400:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


The WiFi chipset is working 100%, I used it on PatredMagic Live CD

---

### Post by chili555 on 2012-12-13
You are going to make me work hard today! Let's dig deeper:```
dmesg | grep -e b43 -e 05:02
```Something simple is wrong and I am going to find it!!

---

### Post by DJAlo on 2012-12-13
Something is missing

> 
alan@alan-TravelMate-2400:~$ dmesg | grep -e b43 -e 05:02
[    0.151067] pci 0000:05:02.0: >[14e4:4318] type 00 class 0x028000
[    0.151087] pci 0000:05:02.0: >reg 10: [mem 0xbc000000-0xbc001fff]
[    1.572149] ssb: Sonics Silicon Backplane found on PCI device 0000:05:02.0
[   19.472917] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   21.720976] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   21.720985] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   21.720988] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.


Should I go on that website and download drivers ? :)

Thanks;)

---

### Post by chili555 on 2012-12-13
Nope. With the ethernet hooked up, do:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet and reboot and let us have your report.

---

### Post by DJAlo on 2012-12-13
You are a God :D everything is working, thank You very much ! :);)

---

### Post by chili555 on 2012-12-13
Excellent! Please use thread tools at the top to mark Solved.

I think you tried *almost* everything...

---

### Post by RaineShadow on 2012-12-24
Thank you so much for your help! I just did this after trying lots and lots of things and this finally got it working. :)

---

### Post by scholzilla on 2012-12-27
I have the same issue, though my chipset is rtl8187. Anyway, I tried the fix offered in message #14 and it didn't help. I've also tried unblocking everything on the rfkill list to no avail. Any other suggestions? fwiw:

```
matt@MT6452:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:d3:d8:d5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.30 duplex=full firmware=N/A ip=192.168.0.2 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:6
       logical name: wlan0
       serial: 00:c0:a8:d8:96:a1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=3.2.0-35-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by chili555 on 2012-12-27
> **scholzilla said:**
> I have the same issue, though my chipset is *rtl8187*. Your post is unlikely to get much attention in a thread titled BCM4318. Please start your own new thread.

---

### Post by scholzilla on 2012-12-28
moved to here: [http://ubuntuforums.org/showthread.php?p=12425410#post12425410](http://ubuntuforums.org/showthread.php?p=12425410#post12425410)

maybe you could help?

---

