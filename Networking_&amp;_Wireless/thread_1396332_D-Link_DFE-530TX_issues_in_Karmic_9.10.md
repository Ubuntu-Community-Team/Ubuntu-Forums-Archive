---
title: "D-Link DFE-530TX issues in Karmic 9.10"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by m3rc on 2010-02-01
I'm trying to add a second NIC to my Karmic 9.10 (Server Edition) as eth1. The new NIC is a D-Link DFE-530TX [http://www.dlink.com/products/?pid=122](http://www.dlink.com/products/?pid=122). It seems like everything should be working fine because it showed up in ifconfig with no configuration after I put it in my machine and it's even is able to get an IP address from the DHCP server in the router. 

The problem is that it's not transmitting anything. I can't SSH into it from my other computers on the LAN, and when I ran a sniffer on the interface it was directly connected to there were no packets.

Here's lspci:

```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)
02:01.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:01.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:07.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 86)
02:0c.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)

```Here's dmesg:

```

[ 3556.000292] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 3556.000551] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3563.384099] eth1: link down
[ 3563.384295] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3566.956016] eth0: no IPv6 routers present
[ 3719.826151] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[ 3719.848746] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3721.988261] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 3721.988534] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3723.377569] eth1: link down
[ 3723.377763] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3732.788010] eth0: no IPv6 routers present
[ 5570.678151] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[ 5570.700746] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5572.988262] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 5572.988540] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5577.373253] eth1: link down
[ 5577.373447] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5583.460028] eth0: no IPv6 routers present
[ 5899.350152] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[ 5899.372754] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 5901.988291] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[ 5901.988566] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 5905.374955] eth1: link down
[ 5905.375148] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 5912.204009] eth0: no IPv6 routers present
[29271.489652] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[29271.512251] ADDRCONF(NETDEV_UP): eth0: link is not ready
[29274.000265] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[29274.000521] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[29278.370782] eth1: link down
[29278.370977] ADDRCONF(NETDEV_UP): eth1: link is not ready
[29284.004008] eth0: no IPv6 routers present
[31708.153652] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[31708.217650] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[31708.273649] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[31711.000263] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[32213.017653] e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
[32213.040246] ADDRCONF(NETDEV_UP): eth0: link is not ready
[32215.000265] e100: eth0 NIC Link is Up 100 Mbps Full Duplex
[32215.000521] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[32218.716171] eth1: link down
[32218.716366] ADDRCONF(NETDEV_UP): eth1: link is not ready
[32225.320167] eth0: no IPv6 routers present

```I was on freenode's #networking IRC channel earlier and someone suggested adding d102e_ucode.bin to the /lib/firmware/e100 directory. After looking around the net for awhile I found the file in the /lib/`uname -r`/e100 folder on my computer and copied it to /lib/firmware/e100. The dmesg above reflects that. 

I hope I've provided enough info and I'd really appreciate any suggestions!

---

### Post by m3rc on 2010-02-02
Dmesg keeps saying 
```
e100 0000:02:0c.0: firmware: requesting e100/d102e_ucode.bin
```

even after I put e100/d102e_ucode.bin in the /lib/firmware directory. Is there any other place where Ubuntu checks for firmware besides /lib/firmware?

---

