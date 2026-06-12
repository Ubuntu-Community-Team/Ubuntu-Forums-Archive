---
title: "Broadcom 4357 any connection at all!"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by cioni on 2010-07-26
Hi everybody,
I am an italian user who wrote already in the italian forum without big results...
I have some problems, like many, with broadcom 4357.
I am a really newbe... I decide to move to ubuntu right 2days ago! I installed the last version (I suppose) from USB in my HP mini 210... everythings is perfect but I cannot connect in any way! wireless doesnt work, neither LAN network. 
I can use both on my windows desktop pc, so is not a network problem... here are some infos maybe you need:

```
*-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:9e:f3:0c:1b
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes  port=MII speed=10MB/s
       resources: irq:27 ioport:5000(size=256)  memory:50010000-50010fff(prefetchable)  memory:50000000-5000ffff(prefetchable)  memory:50020000-5002ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:56000000-56003fff
```pci:

```
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
01:00.0  Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  02)
02:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4357] (rev 01)
```Lan response:

```
listening on LPF/eth0/00:26:9e:f3:0c:1b
sending on LPF/eth0/00:26:9e:f3:0c:1b
sending on socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
no DHCPDISCOVER received
no working leases in persistent database - sleeping.
```I have to say that I have uninstalled network manager and I have installed wicd but I didnt resolve.
I tried to go to hardware/drivers but the list is empty (any STA driver) and it cannot connect, so it cannot download what it needs.
I tried to download by myself the package bcmwl-kernel-source but it says that I need the dkms package... so I tried to install the dkms package, but it says that I need the gcc package (HELP!!!!) so I tried to install the gcc package, but it says that it needs the gcc 4.0-base and I couldnt find it, I found only the gcc 4.0

I found in the broadcome website the drivers, but I am not able at all to install them.
here the link:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

now the question is:
anybody has some suggestions?
somebody could help me to install this driver? (I really have any idea how to do it... I am used to windows!)

please! I am really going insane with this!!
thanks to all ;)

---

### Post by cioni on 2010-07-26
any suggestions :?:

[-o<

---

### Post by cioni on 2010-07-26
up

---

### Post by ewinslow on 2010-08-05
I have a new Acer laptop with the Broadcom 4357 wireless card and it was not working at all after I installed 10.04 LTS. My wired device is Broadcom also and I have not had any trouble with that.
iwconfig showed no wireless interface loaded.
After applying the latest patches the Hardware Drivers interface popped up and asked me if I wanted to install the proprietary driver for the Broadcom wireless interface. I did, rebooted, and my wireless interface was active and working. 
This is also accessed through System->Administration->Hardware Drivers

I'm not sure if this would help at all, but it did get my wireless device going.

---

### Post by ewinslow on 2010-08-05
Here's an update: I'm in the same boat with the wireless. The card is powered up and active, but it can't get an IP address through DHCP. You see the same messages that you posted. My wired connection is having no such issues.

Alas, no solution as of now and it's time for bed. Bummer. Some day I might actually be able to make this install useful. Until then I have to rely on other OSes.

---

### Post by ewinslow on 2010-08-08
Well my connection issue is solved. First part is getting the Broadcom hardwire drivers. Second part is choosing WEP Key instead of WEP Passphrase for the wireless security. That did it.

---

