---
title: "I need help!!!!!! With wireless in xubuntu 9.04"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by unknown23 on 2009-06-03
hello

i have spent hours and hours trying to get my wireless to work in Juanty Jackalope to no avail.

here is my ifconfig and iwconfig output

shadowcast@shadowcast-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:75:80:ef  
          inet addr:192.168.199.105  Bcast:192.168.199.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe75:80ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18581 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19724 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18856412 (18.8 MB)  TX bytes:3003553 (3.0 MB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:263 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13121 (13.1 KB)  TX bytes:13121 (13.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:b7:0c:b3  
          inet6 addr: fe80::290:4bff:feb7:cb3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4235 (4.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-B7-0C-B3-63-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

shadowcast@shadowcast-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"grossenwhn"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: CE:7A:90:4F:4A:93   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

shadowcast@shadowcast-laptop:~$ 

i have the proper driver installed and when i use Wicd, it shows none of the available networks

please help me.

also here is the output for

shadowcast@shadowcast-laptop:~$ hwinfo --netcard
09: PCI 206.0: 0282 WLAN controller                             
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_14e4_4320
  Unique ID: y9sn.6WjBjQYcnn8
  Parent ID: 6NW+.1yBhv2xnpj4
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:06.0
  SysFS BusID: 0000:02:06.0
  Hardware Class: network
  Model: "Hewlett-Packard Company Presario R3000 802.11b/g"
  Vendor: pci 0x14e4 "Broadcom"
  Device: pci 0x4320 "BCM4306 802.11b/g Wireless LAN Controller"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x12fa "Presario R3000 802.11b/g"
  Revision: 0x03
  Driver: "b43-pci-bridge"
  Driver Modules: "ssb"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xe0204000-0xe0205fff (rw,non-prefetchable)
  IRQ: 18 (3324 events)
  HW Address: 00:90:4b:b7:0c:b3
  Link detected: yes
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13 14
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472 2.484
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v000014E4d00004320sv0000103Csd000012FAbc02sc80i00"
  Driver Info #0:
    Driver Status: ssb is active
    Driver Activation Cmd: "modprobe ssb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)

10: PCI 200.0: 0200 Ethernet controller
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8139
  Unique ID: rBUF.GSP5MCus8a6
  Parent ID: 6NW+.1yBhv2xnpj4
  SysFS ID: /devices/pci0000:00/0000:00:1e.0/0000:02:00.0
  SysFS BusID: 0000:02:00.0
  Hardware Class: network
  Model: "Realtek RTL-8139/8139C/8139C+"
  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8139 "RTL-8139/8139C/8139C+"
  SubVendor: pci 0x103c "Hewlett-Packard Company"
  SubDevice: pci 0x3080 
  Revision: 0x10
  Driver: "8139too"
  Driver Modules: "8139too"
  Device File: eth0
  I/O Ports: 0x3000-0x3fff (rw)
  Memory Range: 0xe0208800-0xe02088ff (rw,non-prefetchable)
  IRQ: 16 (714865 events)
  HW Address: 00:c0:9f:75:80:ef
  Link detected: yes
  Module Alias: "pci:v000010ECd00008139sv0000103Csd00003080bc02sc00i00"
  Driver Info #0:
    Driver Status: 8139too is active
    Driver Activation Cmd: "modprobe 8139too"
  Driver Info #1:
    Driver Status: 8139cp is active
    Driver Activation Cmd: "modprobe 8139cp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #16 (PCI bridge)

what am i supposed to do?

by the way, i am a complete xubuntu newbie, i need retard instructions

thanx

---

### Post by unknown23 on 2009-06-03
and i do this... now what?

shadowcast@shadowcast-laptop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4320) present (alternate driver: ssb)
shadowcast@shadowcast-laptop:~$ uname -m
i686
shadowcast@shadowcast-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:75:80:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.199.105 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b7:0c:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:f1:ad:a8:ae:70
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
shadowcast@shadowcast-laptop:~$ sudo gedit /etc/modprobe.d/blacklist
[sudo] password for shadowcast: 
sudo: gedit: command not found
shadowcast@shadowcast-laptop:~$

---

### Post by oellroll on 2009-06-06
I have the same problem with the broadcom bcm4318 in a AMD Turion MT32 with Xubuntu Jaunty on it and I think I install the driver and WICD (network manager installed by me to avoid the default one) detects other wifi networks and it seems that he connects to them but the signal a straight  zero!!!

So please guys out there who have more experience than us, give us a hand, we will be very gratefull and we are already XD

---

### Post by Crafty Kisses on 2009-06-06
Alright so it appears you have the "**Broadcom 4306**" so what you need to do is install ndiswrapper, so install ndiswrapper by running the following:
```
sudo apt-get install ndiswrapper-common
```
Then from there you need to get the proper driver, which I've attached in this post, just look at the bottom of the post and it should be there. So I'm assuming you have downloaded the driver and saved it to your desktop, so open up a Terminal and navigate to your desktop by running:
```
cd /home/username/Desktop
```
Once your there, run the following:
```
ndiswrapper -i bcmwl5
ndiswrapper -m
```
Then once you have done that, make sure the driver is installed. You can do that by running:
```
ndiswrapper -l
```
Now if everything went well, you should get results similar to these:
```
Installed ndis drivers
driver present, hardware present
```
So if those two steps went well, then you need to load the ndiswrapper module so it loads at start, so run the following:
```
sudo modprobe ndiswrapper
```
Now if you installed the **b43-fwcutter** package (that's the firmware) you might have to blacklist it, that's easy though. Just run the following commands in the Terminal:
```
sudo gedit /etc/modprobe.d/blacklist
```
That should open up a text document, and just add the following in that document:
```
blacklist b43-fwcutter
```
Now finally you can try and bring the card up by running the following as root in the Terminal:
```
ifconfig wlan0 up
```
Then of course if that doesn't work, you might need to try and reboot and then try again, you can reboot by:
```
sudo shutdown -r now
```
That will reboot the machine, now remember the driver is attached, and if you follow the steps you should be able to get this wireless card up and running.

---

### Post by RomanIvanov on 2009-06-28
I had the same problem - Xubuntu 9.04 on Dell Vostrol 1510 (Wireless 49454ABG) - does not work wireless. Worked fine for 8.10.

Solution:
just install new xfce 4.6.1

Source link: [http://jeromeg.blog.free.fr/index.php?post/2009/03/04/Installing-Xfce-4.6-on-Ubuntu-8.04-and-Ubuntu-8.10](http://jeromeg.blog.free.fr/index.php?post/2009/03/04/Installing-Xfce-4.6-on-Ubuntu-8.04-and-Ubuntu-8.10)


Run in terminal:
gpg --keyserver keyserver.ubuntu.com --recv 0E23917F5D9DCE6C
gpg --export --armor 0E23917F5D9DCE6C | sudo apt-key add - 

Add in Source code (Application / System /Software Sources -> tab ThirdParty  software)
deb [http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu](http://ppa.launchpad.net/jerome-guelfucci/ppa/ubuntu) jaunty main

Restart the laptop  - work fine.

---

### Post by vkaggal on 2009-06-28
I am glad I came across your post, that did the trick! Thanks very much :KS

> **Codename said:**
> Alright so it appears you have the "**Broadcom 4306**" so what you need to do is install ndiswrapper, so install ndiswrapper by running the following:
```
sudo apt-get install ndiswrapper-common
```Then from there you need to get the proper driver, which I've attached in this post, just look at the bottom of the post and it should be there. So I'm assuming you have downloaded the driver and saved it to your desktop, so open up a Terminal and navigate to your desktop by running:
```
cd /home/username/Desktop
```Once your there, run the following:
```
ndiswrapper -i bcmwl5
ndiswrapper -m
```Then once you have done that, make sure the driver is installed. You can do that by running:
```
ndiswrapper -l
```Now if everything went well, you should get results similar to these:
```
Installed ndis drivers
driver present, hardware present
```So if those two steps went well, then you need to load the ndiswrapper module so it loads at start, so run the following:
```
sudo modprobe ndiswrapper
```Now if you installed the **b43-fwcutter** package (that's the firmware) you might have to blacklist it, that's easy though. Just run the following commands in the Terminal:
```
sudo gedit /etc/modprobe.d/blacklist
```That should open up a text document, and just add the following in that document:
```
blacklist b43-fwcutter
```Now finally you can try and bring the card up by running the following as root in the Terminal:
```
ifconfig wlan0 up
```Then of course if that doesn't work, you might need to try and reboot and then try again, you can reboot by:
```
sudo shutdown -r now
```That will reboot the machine, now remember the driver is attached, and if you follow the steps you should be able to get this wireless card up and running.

---

