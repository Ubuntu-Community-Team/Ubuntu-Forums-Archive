---
title: "eth0 no inet address"
date: 2012-06-13
forum: Networking &amp; Wireless
---

### Post by deus777 on 2012-06-13
I am running Ubuntu Dapper on a file server.  Everything has been working fine until recently, when I couldn't find the server on the network.  The light on the router is on and the lights on the network card are on.  When I do an ifconfig, it looks like this:

eth0 Link encap:Ethernet HWaddr 00:A0:CC:68:ED:BD
     inet6 addr: fe80::2a0:ccff:fe68:edbd/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:33 errors:1 dropped:0 overruns:0 carrier:2
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 b) TX bytes:9702 (9.4 KiB)
     Interrupt:10 Base address:0xe400

lo Link encap:Local Loopback
   inet addr:127.0.0.1 Mask:255.0.0.0
   inet6 addr: ::1/128 Scope:Host
   UP LOOPBACK RUNNING MTU:16436 Metric:1
   RX packets:3 errors:0 dropped:0 overruns:0 frame:0
   TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
   collisions:0 txqueuelen:0
   RX bytes:172 (172.0 b) TX bytes:172 (172.0 b)

if I ping my router, I get this:
connect: Network is unreachable

if I run dhclient eth0, I get this:
Listening on LPF/eth0/00:a0:cc:68:ed:bd
Sending on LPF/eth0/00:a0:cc:68:ed:bd
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I have tried ifdown eth0, ifup eth0 and I have tried restarting the server and neither has done anything to fix the problem.

Does anyone have any suggestions?

Thanks

---

### Post by poolet on 2012-06-13
First try to restart your refresh your network:: 

```
/etc/init.d/networking stop and then after 30 sec start
```or 
```
/etc/init.d/networking restart
```then check the following:: 
```
 /etc/network/interfaces
```Static IP example::

[LIST]
[*]auto lo
[*]iface lo inet loopback
[*]auto eth0 iface eth0 inet static
[*]address 208.88.34.106
[*]netmask 255.255.255.248
[*]broadcast 208.88.34.111
[*]network 208.88.34.104
[*]gateway 208.88.34.110
[/LIST]
 Please check the link below, you will find a bunch of information's about network configuration if doesn't helps you please open a new terminal and type the following:: 
```
lshw -C network
``` at the end paste the output..!!

**Your link/source**:: [http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialNetworking.html)

Good Luck!!

---

### Post by Cheesehead on 2012-06-14
> **deus777 said:**
> 
     TX packets:[COLOR="Red"]33 errors[/COLOR]:1 dropped:0 overruns:0 carrier:2


This may be hardware (cable or interfaces going bad)...or it may just be autonegotiation has failed. Try unplugging and re-plugging the network cable, which will force the hardware to renegotiate the connection.

---

### Post by poolet on 2012-06-14
> **Cheesehead said:**
> This may be hardware (cable or interfaces going bad)...or it may just be autonegotiation has failed. Try unplugging and re-plugging the network cable, which will force the hardware to renegotiate the connection.

If autonegotiation failed.. You can try the following::

```
sudo apt-get install ethtool
``````
sudo ethtool eth0 Settings for eth0:
```if Supports auto-negotiation & Advertised auto-negotiation are set **yes** and your using **half duplex** continue with the followings!! 

```
sudo mii-tool eth0 eth0: autonegotiation failed, link ok
``````
ethtool -s eth0 speed 100 duplex full autoneg off
``````
iface eth0 inet static pre-up /usr/sbin/ethtool -s eth0 speed 100 duplex full autoneg off
```

---

### Post by deus777 on 2012-06-15
Restarting networking did not appear to fix the problem.

This is what my /etc/network/interfaces looks like:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Here is the output from lshw -C network:
[171618.419109] Buffer I/O error on device hdb, logical block 0
[171618.422901] Buffer I/O error on device hdb, logical block 1
[171618.426594] Buffer I/O error on device hdb, logical block 2
[171618.430148] Buffer I/O error on device hdb, logical block 3
 *-network
  description: Ethernet interface
  product: LNE100TX [Linksys EtherFast 10/100]
  vendor: Lite-On Communications Inc
  physical id: 9
  bus info: pci@00:09.0
  logical name: eth0
  version: 25
  serial: 00:a0:cc:68:ed:bd
  width: 32 bits
  clock: 33Mhz
  capabilities: bus_master cap_list ethernet physical
  configuration: broadcast=yes driver=tulip driverversion=1.1.13 multicast=yes
  resources: iopoort:e400-e4ff iomemory:e9020000-e90200ff irq:10

---

### Post by deus777 on 2012-06-15
I tried unplugging and re-plugging the network cable, followed by ifdown eth0 and ifup eth0, but the results were the same.

edit: I tried a different network cable as well, followed by ifdown and ifup.  Same results.

When I ran ethtool eth0 I got:
Settings for eth0:
No data available

---

### Post by poolet on 2012-06-16
> **deus777 said:**
> 

Here is the output from lshw -C network:
[171618.419109] Buffer I/O error on device hdb, logical block 0
[171618.422901] Buffer I/O error on device hdb, logical block 1
[171618.426594] Buffer I/O error on device hdb, logical block 2
[171618.430148] Buffer I/O error on device hdb, logical block 3
 ..............................

First of all, I think you **must **backup your data as soon as possible,and replace your hard drive with a new one.. Seems that your hardware have bad sectors. you can run and check if there are bad sectors by:: 

```
sudo badblocks -v /dev/'type'
``` //*type example: sda*//
as for your network problem, are you using external network card ??? 

please check the ```
lsusb 
```

---

### Post by deus777 on 2012-06-22
poolet:
Thanks for the concern about my HDD, but fstab reports that hdb is my internal CD-ROM drive, so I don't think it's a problem.

The network card is a PCI internal network card.

---

### Post by deus777 on 2012-07-04
I think I've found the problem.  Apparently I never tried a different port on my router.  When I switched the cable to a different port, the ethernet card was able to get a DHCP response.

This is the second Linksys WRT54GL that I've had strange issues with.  They seem to last 3-5 years and then start having hardware issues.  Can anyone suggest a reliable replacement?

---

