---
title: "weak/unstable wireless connection"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by guibon on 2010-05-24
Hello everybody,

I understand that wireless is one of the most common problems with Linux, although I did not have this experience with past distributions or versions.

After two years away from Ubuntu I installed 10.04 and everything is working fine except the wireless connection.

Actually, it does work and connect, but goes up and down, loses connection and in most cases does not reconnect, unless I am 1 meter from the router. The room next door is already too far, a place where I normally have my laptop connecting perfectly with XP.

I am using a Toshiba M70,some additional information below:

lspci=

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:04.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:04.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:04.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:04.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:e2:c4:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:13:ce:ad:25:c2  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fead:25c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5869 errors:2 dropped:2 overruns:0 frame:0
          TX packets:5906 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5816087 (5.8 MB)  TX bytes:876521 (876.5 KB)
          Interrupt:22 Base address:0x4000 Memory:c4007000-c4007fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"reetwerder15"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:A7:B0:A4   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=67/100  Signal level=-52 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:0   Missed beacon:


I hope this is not too much information to start with. Although I have used Linux before, i would consider myself a newby, as i am acquainted with GUI but not so much with console.

Thanks for any help, I have found lots of wireless and even ipw2200 topics, but none seem to be quite the problem I seem to have.

Thanks for any help!

---

### Post by guibon on 2010-05-26
I was going to reinstall 10.04 and went to check out the live cd. And amazingly I had much more stable connection, even in the room next door.

I then went and installed directly from out of the live version and was spectator to when the installation got to the part of configuring my wireless connection. Right at that moment the connection was interrupted and I am back to the unstable ups and downs, with absolutely no connection once I am more than a meter away from the router. 

Its just an observation of which I hope someone might see the cause of my problem. Could be a driver problem?

Thanks again for any support.

---

### Post by cariboo on 2010-05-26
Boot from the Live CD then check to see what driver your wireless device is using. Open a terminal and type:

```
sudo lshw -C network
```

The output should look similar to this:

```
description: Ethernet interface
       product: MCP61 Ethernet
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: a2
       serial: 00:24:21:b7:69:49
       size: 100000000
       capacity: 100000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver**=forcedeth driverversion=0.64 duplex=full ip=192.168.1.225 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:27 memory:dee7d000-dee7dfff ioport:de00(size=8)
```

I've highlighted the driver, in my case it is a forcedeth. Note what driver is being used, then check with your install to see if it is using the same driver.

---

### Post by guibon on 2010-05-26
> **cariboo907 said:**
> Boot from the Live CD then check to see what driver your wireless device is using. Open a terminal and type:

```
sudo lshw -C network
```The output should look similar to this:

.

Hello cariboo907, thanks for your reply. using the above command I received the following output

*-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:ad:25:c2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.101 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:22 memory:c4007000-c4007fff


I will go back and boot the normal Ubuntu partition, to compare the drivers. Will post here in a moment.

Thanks!

---

### Post by guibon on 2010-05-26
> **cariboo907 said:**
> Boot from the Live CD then check to see what driver your wireless device is using. Open a terminal and type:

```
sudo lshw -C network
```The output should look similar to this:

.

And this is what I get, when I log in the installed version.

network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:ad:25:c2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.101 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11g
       resources: irq:22 memory:c4007000-c4007fff

As far as I can tell at first sight it's the same driver. So the only difference that remains between live cd and installed version would be the updates it loaded during installation? 

Luckily for me, unfortunately for testing, I am currently at the office, the wifi signal only has to cross a hollow wall: I have a permanent connection. But it still bumps around between 94%, 52% and even 0% signal strength every 5 seconds.

Again, thanks a lot for any help.

Edit: while writing the above, my wireless lost signal again, asked for the WPA key, tried to connect again, asked for the key again and then said, it was now disconnected. It will not reconnect at all, I am now back on ethernet...

---

### Post by Phocean on 2010-05-26
My connection is very unstable too. I reported a bug : [https://bugs.launchpad.net/ubuntu/+bug/583210](https://bugs.launchpad.net/ubuntu/+bug/583210).

My driver is iwlagn, this is maybe not the problem after all. I had been using another Linux distro on my laptop for months (openSUSE 11.1 and 11.2), which come with the same driver, without any issue.

What has been messed up ?

---

### Post by hmjbarbosa on 2010-07-27
Did anyone find a solution???

I am having the very same problem. I am only 3 meters away from the router and ubuntu signal is at 44% oscilating alot and loosing connection every 5 minutes or so. When dual booting into windows XP, there's no problem at all. Signal is at 100% and I can transfer files at my ISP connection limit.

My configuration is:

HP Pavillion zv2000
Dual boot: Windows XP and Ubuntu 10.04
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:5c:0c:ca
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.41 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:d4000000-d4000fff
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:06:92:00
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:d4100000-d4100fff ioport:3000(size=64)

---

### Post by Phocean on 2010-07-28
Have you ever customized your wireless settings?
For some reason the driver included with Ubuntu is very sensitive to some settings.
See the bug history: [https://bugs.launchpad.net/ubuntu/+bug/583210](https://bugs.launchpad.net/ubuntu/+bug/583210)
and feed it if you have the same kind of issue...

---

