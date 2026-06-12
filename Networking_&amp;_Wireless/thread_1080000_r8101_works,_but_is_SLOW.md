---
title: "r8101 works, but is SLOW"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by davewilliam on 2009-02-24
I managed to grab the realtek driver r8101 from their site, build it, and installed it.  However, network transfers are incredibly slow.  

Using smbclient to transfer from a windows share, i average 500KB/s.  However if I use wget to grab a Ubuntu iso, I can usually get 1MB/s.  Other machines on my network can transfer an order of magnitude faster!  So what's the deal? 

Here's some info:

```
uname -a
Linux myServer 2.6.27-11-server #1 SMP Thu Jan 29 20:19:41 UTC 2009 i686 GNU/Linux
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:6f:7d:f2  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe6f:7df2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73133702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47595804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:897152906 (897.1 MB)  TX bytes:2890779276 (2.8 GB)
          Interrupt:16 Base address:0xc000
```

```
modinfo r8101
filename:       /lib/modules/2.6.27-11-server/kernel/drivers/net/r8101.ko
version:        1.011.00-NAPI
license:        GPL
description:    RealTek RTL-8101 Fast Ethernet driver
author:         Realtek and the Linux r8101 crew <netdev@vger.kernel.org>
srcversion:     3707A2834AE878D0A712D76
alias:          pci:v000010ECd00008136sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.27-11-server SMP mod_unload modversions 686 
parm:           speed:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           duplex:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           autoneg:force phy operation. Deprecated by ethtool (8). (array of int)
parm:           rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm:           use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm:           debug:Debug verbosity level (0=none, ..., 16=all) (int)
```


```
lshw -C network
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:6f:7d:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8101 driverversion=1.011.00-NAPI duplex=full ip=192.168.0.2 latency=0 link=yes module=r8101 multicast=yes port=twisted pair speed=100MB/s
```


```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
04:00.0 Mass storage controller [0180]: Promise Technology, Inc. PDC40718 (SATA 300 TX4) [105a:3d17] (rev 02)
```


I'm wide open for suggestions.  I built this machine to be my network file server.  But it's kind of pointless when i go to transfer a 5GB file and when i get home from work and it's still not done!

I have tried various network cables and various ports in  my router.  I don't think it's a router issue as every other machine transfers files back and forth much quicker.  

Motherboard is the D945GCLF.

thanks

---

### Post by davewilliam on 2009-03-02
Update:

Using iperf between my ubuntu box and my winxp box shows transfer rates of 33Mb/s.

FTP to the ubuntu box is never very consistant, anywhere from 200KB/s to 4MB/s.

My router is running DD-WRT v23 SP2, but i don't know if that is playing an issue.

Mid-update update:

It's on the XP side of things.  (Not sure what yet)

update:

Yep, new windows drivers did the trick.

---

### Post by AlexTheStampede on 2009-08-30
Hi, hoping this isn't considered necro-posting, i have pretty much the same issue. Only that i get 20-40 kilobytes of speed for lan transfers.
Motherboard is the same (Intel D945GCLF) but i'm on Ubuntu 9.04 fully updated as of today.
However, i did some tests, i plugged in two different 10/100 eth cards (no luck) and even a wifi usb dongle (seriously, it seems like network capping!). Funny enough, it goes faster if it's only a matter of moving data to and from the internet.
SMB sucks horribly, takes a second or so to show the contents of a semi-empty folder. SSH sharing with a good SFTP client has no real issues with showing folder contents up to say, 50 items, but that's where i measured the transfer speeds. Not good.
Now, sum those things with the fact that in the very beginning of 9.04 i COULD get up to 90Megabits of down speed locally with the aforementioned SSH way (SMB always sucked) and that CPU usage is fine even while using VNC (oh god, it's so slow!), and you'll see why i'm frustrated and pissed off.
Please, please PLEASE help me, it's very uncool to move files with an USB drive because it's faster than the network. Especially in cases where i could just stream the files from the server instead of having to copy it locally...
My level of experience is enough to copy-paste commands in the terminal, i can ssh in from a different machine, there should be everything needed to compile stuff (hopefully useless), my Mac has been just updated to Snow Leopard after a good formatting (no risk of lingering issues like that! :D ), i have NO access to any Windows box real or virtual and finally, i'm out of money so i can't just "disable the integrated NIC from the bios and go buy a gigabit adapter".

---

### Post by AlexTheStampede on 2009-09-01
Update/bump.
Speed dosen't get better in a Linux to Linux transfer. Nor with other SFTP clients.
Lately it did something wrong to the internet connectivity, too... i tested my ISP for torrent blocks (24 hours to NOT download latest Azureus update... something is wrong, it's not like i got slow torrents) and on another computer everything is cool and fine, while on that one i directly get a "connection lost" during the test ( [http://broadband.mpi-sws.org/transparency/bttest.php](http://broadband.mpi-sws.org/transparency/bttest.php) )

Again, help please?

---

### Post by AlexTheStampede on 2009-09-23
Found the issue, completely by mistake. The router it was plugged into was getting close to the end of it's life span... removed that thing, everything works as it should.

---

