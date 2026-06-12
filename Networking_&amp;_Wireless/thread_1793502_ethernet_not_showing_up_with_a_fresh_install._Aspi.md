---
title: "ethernet not showing up with a fresh install. AspireOneD255E"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by HELLO_science on 2011-06-29
I have installed ubuntu, xubuntu on this laptop with usb drives and even net install wont work.  Once the os gets installed i see no indication that the ethernet is even there...
lspci:
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

ifconfig:
eth0      Link encap:Ethernet  HWaddr 90:00:4e:97:9b:9d  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe97:9b9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1878 errors:0 dropped:0 overruns:0 frame:1766
          TX packets:1610 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1426246 (1.4 MB)  TX bytes:340278 (340.2 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

------

My wireless works with Broadcom support.  The ethernet has never worked, i think when windows was still on it, it did.

'been scratching my head...

---

### Post by chili555 on 2011-06-29
> 01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)> [COLOR="Red"]eth0[/COLOR] Link encap:Ethernet HWaddr 90:00:4e:97:9b:9d
inet addr:192.168.0.112 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::9200:4eff:fe97:9b9d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1That's a pretty good indication that ethernet is up, attached and has an IP address. Do you have some reason to believe otherwise? It is exceedingly rare for ethernet to be other than eth0. May we see:```
sudo lshw -C network
```

---

### Post by HELLO_science on 2011-06-29
sudo lshw -C network

  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:57000000-5703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 90:00:4e:97:9b:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.0.112 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:56000000-56003fff


...

Yes, it seems that my ethernet is working but i belive the eth0 listing from lspci is refering to my wireless...

when i plug an ethernet cord (that is a good working cord, tested) i get no "WIRED" selection from network-manager from the panel or in the program.  Even net installs havent worked with this machine (probably related issue but not sure)

---

### Post by chili555 on 2011-06-29
> i belive the eth0 listing from lspci is refering to my wireless...
I believe you're exactly correct. In about a gazillion posts on this forum, I've seen this exactly twice. It hurts nothing but does make life a bit more interesting. Please run and post:```
lspci -nn | grep Atheros
modinfo atl1c
sudo modprobe atl1c
dmesg | grep atl
```That's a bit confusing, it's lower-case for ATLoneC.

You didn't mention the Ubuntu version you installed; 11.04, 10.10, 6.04, et al. Older versions don't include atl1c and require that it be compiled from scratch. Here is the rough process at post #6:  [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)

Before you hitch up the plasma cutter and get busy, let's fine-tune the instructions and know if they're even needed.

---

### Post by nm_geo on 2011-06-29
This is going to be interesting.  Glad you grabbed it again, I was just about to recommend that link too.  Go figure a Broadcom wireless comes right up and ethernet connection not found.

---

### Post by chili555 on 2011-06-29
> Go figure a Broadcom wireless comes right up and ethernet connection not found."You have just crossed over into the Twlight Zone." Or maybe a parallel universe. I hope my ex-wife's lawyer is still...oh, never mind.

---

### Post by nm_geo on 2011-06-29
> **chili555 said:**
> "You have just crossed over into the Twlight Zone." Or maybe a parallel universe. I hope my ex-wife's lawyer is still...oh, never mind. Mine two.. ex-wives that is..  I pray there ain't no parallel..  LOL

---

### Post by HELLO_science on 2011-07-01
as per chilli555:

datura@datura-laptop:~$ lspci -nn | grep Atheros
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
datura@datura-laptop:~$ modinfo atl1c
filename:       /lib/modules/2.6.32-32-generic/kernel/drivers/net/atl1c/atl1c.ko
version:        1.0.0.1-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Jie Yang <jie.yang@atheros.com>
srcversion:     B679B4EF678AB94A69C067B
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-32-generic SMP mod_unload modversions 
datura@datura-laptop:~$ sudo modprobe atl1c
[sudo] password for datura: 
Sorry, try again.
[sudo] password for datura: 
Sorry, try again.
[sudo] password for datura: 
Sorry, try again.
sudo: 3 incorrect password attempts
datura@datura-laptop:~$ sudo modprobe atl1c
[sudo] password for datura: 
datura@datura-laptop:~$ dmesg | grep atl
datura@datura-laptop:~$ dmesg | grep atl


-------------------

I installed from 9somthing, then upgraded to 10.04, now im using karmic repositories,,, I'm not sure the command to check the version...

incase anyone didnt catch this: when i went for a netinstall using the ethernet port (after having linux already on the device) it wouldnt even DHCP.  like noones home.

Thanks for all the help, it really means alot to me,,, we have just ethernet at the house

---

### Post by chili555 on 2011-07-01
You have the driver atl1c on your system and it loaded without complaint. Does an ethernet interface appear?```
ifconfig
```Any clues here?```
dmesg | grep -e Atheros -e 01:00
```Please run:```
lspci -nn
```When you see the pci.id, a couplet like 1969:456b or some such, please confirm that it's listed in the aliases for atl1c:> alias: pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]1062[/COLOR]sv*sd*bc*sc*i*
alias: pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]1063[/COLOR]sv*sd*bc*sc*i*If not, then Plan B!

---

### Post by HELLO_science on 2011-07-01
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)

--------
[    0.554635] pci 0000:01:00.0: reg 10 64bit mmio: [0x57000000-0x5703ffff]
[    0.554654] pci 0000:01:00.0: reg 18 io port: [0x5000-0x507f]
[    0.554765] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.554779] pci 0000:01:00.0: PME# disabled


-------------
datura@datura-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
-------




I like where with the second command the word "disabled" is used,

---

### Post by nm_geo on 2011-07-01
> I installed from 9somthing, then upgraded to 10.04, now im using karmic  repositories,,, I'm not sure the command to check the version...

I be confused by this.. Run this code please..

```
cat /etc/lsb-release
```

---

### Post by chili555 on 2011-07-01
> 01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [[COLOR="Red"]1969:2060[/COLOR]] (rev c1)Well, as you can see, your device is not listed in the aliases for atl1c:> $ modinfo atl1c
filename: /lib/modules/2.6.32-32-generic/kernel/drivers/net/atl1c/atl1c.ko
version: 1.0.0.1-NAPI
license: GPL
description: Atheros 1000M Ethernet Network Driver
author: Jie Yang <jie.yang@atheros.com>
srcversion: B679B4EF678AB94A69C067B
alias: pci:v00001969d00001062sv*sd*bc*sc*i*
alias: pci:v00001969d00001063sv*sd*bc*sc*i*
depends:
vermagic: 2.6.32-32-generic SMP mod_unload modversions The vendor is listed, 1969, but the specific device, 2060 is not. In later versions, it is listed:> $ modinfo atl1c 
filename:       /lib/modules/2.6.38-8-generic/kernel/drivers/net/atl1c/atl1c.ko
version:        1.0.1.0-NAPI
license:        GPL
description:    Atheros 1000M Ethernet Network Driver
author:         Jie Yang <jie.yang@atheros.com>
srcversion:     C57BE61DF80AB32F928DEB3
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v00001969d00001073sv*sd*bc*sc*i*
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v0000[COLOR="Red"]1969[/COLOR]d0000[COLOR="Red"]2060[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.38-8-generic SMP mod_unload modversions 686 We have two options. One is to install a later version of Ubuntu and the other is to download and compile the driver from source. You have wireless, so downloads are possible. Which do you prefer?

---

### Post by chili555 on 2011-07-01
> **nm_geo said:**
> I be confused by this.. Run this code please..

```
cat /etc/lsb-release
```He's pretty clearly running 10.04:> $ modinfo atl1c
filename: /lib/modules/[COLOR="Red"]2.6.32-32-generic[/COLOR]/kernel/drivers/net/atl1c/atl1c.ko
version: 1.0.0.1-NAPI
license: GPL

---

### Post by nm_geo on 2011-07-01
I agree I checked the kernel too.  What threw me was the karmic repositories not Lucid?

---

### Post by HELLO_science on 2011-07-03
thanks for the great help with this funky issue.
        
I'd like to have the ethernet driver already compiled but if that turns into an expedition i'm familiar with compiling simple C++ code and id imagine i'd use g++ sort of the same way (?)

10.04 lts

---

### Post by chili555 on 2011-07-03
> I'd like to have the ethernet driver already compiled I would, too, however, the only person that can compile the driver against your kernel and your version of gcc is you. > if that turns into an expedition i'm familiar with compiling simple C++ code and id imagine i'd use g++ sort of the same way (?)Well, it's not nearly that complex. Let's get started. With an internet connection, wireless, I assume, open Applications > Accessories > Terminal and do:```
sudo apt-get install build-essential linux-headers-generic
```Now download the two files I've attached to your desktop.

Open a termianl and do:```
cd Desktop
mkdir driver
mv AR81* driver
cd driver
tar zxf AR81Family-linux-v1.0.1.14.tar.gz
tar zxf AR81Family-linux-v1-1.0.1.14.patch.tar.gz
mv AR81Family-linux-v1-1.0.1.14.patch src
cd src
patch -p1 < AR81Family-linux-v1-1.0.1.14.patch
cd ..
sudo make
sudo make install
sudo modprobe atl1e
```Please stop and ask if you get stuck or encounter an error. It makes oh so perfectly on my 11.04 system.

---

