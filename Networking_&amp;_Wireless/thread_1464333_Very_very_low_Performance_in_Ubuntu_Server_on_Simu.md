---
title: "Very very low Performance in Ubuntu Server on Simultanious TCP(FTP) operation"
date: 2010-04-28
forum: Networking &amp; Wireless
---

### Post by ranjish on 2010-04-28
[COLOR=black][FONT=Verdana]Hi all,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
**[COLOR=black][FONT=Verdana]Ubuntu System Configuration: [/FONT][/COLOR]**
[COLOR=black][FONT=Verdana]Ubuntu9.10[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Kernel version: 2.6.31-20 generic[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]RAM: 1GB[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Intel Dual Core Processor[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Ubuntu : Used as FTP server[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Clinet : Windows Machine[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Utilites used: Iperf, ftp[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[FONT=Verdana]When I’m [COLOR=black]performing Simultaneous TCP upload and Download the throughput is very very low.[/COLOR][/FONT]
[FONT=Verdana]When I’m performing TCP download alone I am able to get very good throughput. (Tested via iperf utility)
When I’m [COLOR=black]performing TCP upload alone I am able to get very good throughput. (Tested via iperf utility)[/COLOR][/FONT]
[COLOR=black][FONT=Verdana]When Simultaneous UDP Upload and Download is performed the throughput is as expected.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[FONT=Verdana]Since the default settings were not giving good results in simultaneous throughput, I tried to tweak the kernel tcp ,core, ipv4 parameters as mentioned in [/FONT][FONT=Verdana][http://ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux](http://ubuntulinuxhelp.com/speed-up-your-internet-connection-in-ubuntu-linux)[/FONT]
[COLOR=black][FONT=Verdana]And still no improvement in simultaneous throughput.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When I switched the server to a Windows 2000 server, I get very good throughput in Simultaneous TCP upload/download and FTP upload/download.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Can any one help me out on getting best simultaneous TCP upload and download results on Ubuntu.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Are there any special tools or what settings should be changed to achieve the best simultaneous throughput?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
--RaNjIsH

---

### Post by P4man on 2010-04-28
sounds like your network card is not in full duplex, its probably a driver related issue. What network card is this? Can you post the output of

```
dmesg | grep "eth"
```

and

```
lspci
```

---

### Post by ranjish on 2010-04-28
> **P4man said:**
> sounds like your network card is not in full duplex, its probably a driver related issue. What network card is this? Can you post the output of

```
dmesg | grep "eth"
```

and

```
lspci
```
$ dmesg | grep eth
[ 1.518636] eth0: RealTek RTL8139 at 0x2000, 00:03:0d:6b:e1:a6, IRQ 16
[ 14.949852] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 25.760050] eth0: no IPv6 routers present
 
$lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
06:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by P4man on 2010-04-28
Yep, half duplex, and only 10Mbit! No wonder its slow.

Can you try running these commands in a terminal and see if that forces 1gbit full duplex?

```
sudo ifdown eth0
sudo ethtool -s eth0 speed 1000 duplex full autoneg off
sudo ifup eth0
```

If you dont have a gigabit router, change the 1000 in to 100.

---

### Post by nic.de.muyer on 2010-04-28
10Mbit half-duplex for an FTP server ... holy yikes :shock:

Since this seems a bizar setting to configure manually, I wonder whether the switch to which your ftp server is connected, is proposing this value through autonegotiating.

Use mii-tools / ethtool to switch your card to 100Mbit Full Duplex, but stating the above, it might be very well possible that the switch will cut you off (depending on how the switch has been configured).  If so, ask the network admins to reconfigure the port.

---

### Post by P4man on 2010-04-28
I should have mentioned this, the first command will kill the network connection, so if you are doing this remotely, you will lose the connection. I hope you have physical access to it or a way to remote reboot if not...
> 
wonder whether the switch to which your ftp server is connected, is proposing this value through autonegotiating.

Since windows uses correct values (I assume at least) I think its a problem with the driver, unless windows overrides the switch or router's autoneg values..

---

