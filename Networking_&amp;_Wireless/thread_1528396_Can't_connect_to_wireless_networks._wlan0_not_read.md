---
title: "Can't connect to wireless networks. wlan0 not ready."
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by kzinjuwadia on 2010-07-10
Subject: Can't connect to wireless networks. wlan0 is not ready. AP is always not associated.

Hi all,

I've installed fresh Ubuntu 10.04 after partitioning WinXP on my PC. I've Netgear MA101 (Rev.B) wireless adapter connected via USB port. adapter works fine on WinXP. When connected ubuntu asked to download the firmware to use the adapter, which I did. Now, I can see the wireless networks in range via network manager and wicd (yes I ended up installing it too hoping to fix my problem).

However, I'm not able to connect to my wireless network (WEP protected) or other unsecured networks which I'm using on my laptop simultaneously. It tries for sometime and then quits. After research I found that wlan0 on my PC is not ready. Maybe due to which "Access Point" in iwconfig always says "Not associated", no matter whatever I do. I tried a lot of thing to fix this with no success. Hence, now I've to bug you guys to help me fix this. Here are some details that I think with help you understand the problem.

Thanks in advance for your help.

kzinjuwadia@kzinjuwadia-desktop:/etc$ sudo lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0864:4102 NetGear, Inc. MA101 802.11b Adapter <<< adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

kzinjuwadia@kzinjuwadia-desktop:/etc$ sudo lsmod 
Module                  Size  Used by
arc4                    1153  2 
. . .
mac80211              204922  1 at76c50x_usb << looks good to me
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
cfg80211              126485  1 mac80211
psmouse                63245  0 
. . .
kzinjuwadia@kzinjuwadia-desktop:/etc$ sudo iwconfig wlan0 
wlan0     IEEE 802.11b  ESSID:"Shubham"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

kzinjuwadia@kzinjuwadia-desktop:/etc$ sudo iwlist wlan0 scan
. . .
  Cell 04 - Address: 00:11:50:3B:BE:93 <<< Wireless network I'm trying to connect to
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=11/100  Signal level=11/100  
                    Encryption key:off
                    ESSID:"Shubham"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000289b60372d3
                    Extra: Last beacon: 188ms ago
                    IE: Unknown: 00075368756268616D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010000

Using "sudo iwconfig wlan0 ap any" doesn't fix it.

dmesg snippet:
[ 4961.787003] wlan0: direct probe to AP 00:11:50:3b:be:93 (try 1)
[ 4961.974248] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 4961.984181] wlan0: direct probe to AP 00:11:50:3b:be:93 (try 2)
[ 4962.184092] wlan0: direct probe to AP 00:11:50:3b:be:93 (try 3)
[ 4962.384046] wlan0: direct probe to AP 00:11:50:3b:be:93 timed out
[ 4966.673450] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4966.863933] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

kzinjuwadia@kzinjuwadia-desktop:/etc$ sudo ifconfig wlan0 up
kzinjuwadia@kzinjuwadia-desktop:/etc$ sudo ifup wlan0 
ifup: interface wlan0 already configured
kzinjuwadia@kzinjuwadia-desktop:/etc$ cat /etc/network
network/  networks  
kzinjuwadia@kzinjuwadia-desktop:/etc$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
allow-hotplug wlan0
iface wlan0 inet dhcp

I think the driver etc is fine and there's something wrong with configuration. I don't have any wpa_xxx.conf file as I thought I'd need it only if I want to connect to a wpa-protected wireless network.

---

### Post by kzinjuwadia on 2010-07-10
I read on another post here and some more cmds were asked for. I thought of putting them here to save time. Awaiting response for the forum.


kzinjuwadia@kzinjuwadia-desktop:/etc$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 10
       serial: 00:e0:18:8b:62:11
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.5 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:a000(size=256) memory:e8800000-e88000ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:09:5b:10:3c:a7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

"WirelessEnabled" is true in /var/lib/NetworkManager/NetworkManager.state

---

### Post by kzinjuwadia on 2010-07-11
Can someone be kind enough to reply? Even some clues to dig further will be appreciated. Do I need wpa_supplicant for wlan0 to be ready?

Thanks

---

### Post by gimmickless on 2010-08-15
I'm having the same problem you are.  The MAC for my wireless card is 00:17:3f:9a:53:e2.

I also inputted information as per [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834) . The only difference is that I left "iface wlan0 inet dhcp" as the second line in /etc/network/interfaces.

---

