---
title: "Network Setup - Internet Sharing with Wireless"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by throwingks on 2009-01-21
This is what I have in mind.

[Cable Modem] --- [Ubuntu Server 8.04 w/ Webmin] --- [Linksys WRT54G (DD-WRT Micro)] -(wireless)- [Xubuntu 8.04 laptop (wlan0 in) & (eth0 out)] --- [Wired Router] --- [3 Devices]

I have been reading and trying for 3 days. All I can get right now is the 3 final devices to ping eachother. But, there is no internet access. Does anyone have any advice to make this work?

I included an image to help visualize what is going on.

---

### Post by bgerlich on 2009-01-21
1. Can Xubuntu ping the wired router?
2. Can Xubuntu ping the Linksys ?
3. Can Ubuntu Server ping the Linksys ?
4. Can Ubuntu Server ping anything on the internet (4.2.2.1 for example)?

---

### Post by throwingks on 2009-01-21
It depends how everything is hooked up. Right now, the Ubuntu w/ Webmin is turned off and the Linksys is DHCP server. So, the Xubuntu and another (not mentioned) wireless laptop on the Linksys can both access the internet. The WinXP pc and Xboxes cannot. I am having trouble getting webmin to assign addresses, so it is easier to have it off right now. I will turn it back on once I get the wired router setup correctly.

I am willing to format everything and start fresh. I am also willing to give everything a static IP if necessary.

---

### Post by bgerlich on 2009-01-21
the problem is your wireless connection on Xubuntu.
Type in "sudo lshw -C network" , "route", "iwconfig" on your Xubuntu machine and post the output.

---

### Post by Iowan on 2009-01-21
You've probably seen [this]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") one - but in case not...

---

### Post by throwingks on 2009-01-21
I have, but I don't want to use Firestarter. I am using Ubuntu-Server w/ Webmin for firewall and DHCP. There is no GUI. I may have to install XFCE if I get frustrated enough.

I have lost my Internet Access on the Xubuntu laptop now. I will post those logs when I get it back up.

---

### Post by throwingks on 2009-01-25
> **bgerlich said:**
> "sudo lshw -C network"```
  *-network               
       description: Realtek
       physical id: 0
       version: Rtl8139
       slot: Socket 0
       resources: irq:10
  *-network
       description: 10/100 Port Attached PC Card
       product: 1.0
       vendor: Dual Speed
       physical id: 0
       slot: Socket 1
       resources: irq:3
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 20
       serial: 00:0c:41:a7:85:7f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lsrtnds driverversion=1.52+Cisco-Linksys, LLC.,10/01/2 ip=192.168.1.122 latency=64 link=yes maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:e0:98:98:21:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=pcnet_cs ip=192.168.10.10 multicast=yes

```> "route"```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 wlan0
192.168.10.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         DD-WRT          0.0.0.0         UG    0      0        0 wlan0
default         192.168.10.254  0.0.0.0         UG    0      0        0 eth0
```> "iwconfig"```
lo        no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"ThrowingKs"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:BF:CE:AC:D5   
          Bit Rate=11 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:21/100  Signal level:-82 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:-883286272  Invalid misc:-862194398   Missed beacon:0

eth0      no wireless extensions.
```

I also installed firestarter to this machine and dhcp3. The XP machine pulls an ip from the DHCP server, but does not get on the internet.

---

