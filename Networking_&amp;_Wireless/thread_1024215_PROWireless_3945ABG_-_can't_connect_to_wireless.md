---
title: "PRO/Wireless 3945ABG - can't connect to wireless"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by eplemonster on 2008-12-28
Hello!

I just recently installed Ubuntu 8.10 on my laptop, and everything works perfectly except my wireless connection. The drivers for the wlan card seem to work, at least they are correctly installed as PRO/Wireless 3945ABG, but I can't connect to any wireless networks. In fact, the network manager gui doesn't even display any wireless network (it used to). I was wondering if you could please help me out. I'd love to replace Windows with Ubuntu, but in order to make that happen I need a working wireless connection :)

I'll give you some output:

[QUOTE="iwconfig"]

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.[/QUOTE] 

[QUOTE="lshw -C network"]
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:37:ae:dd
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:fc:92:99
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.159 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:8d:cd:b3:6c:38
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
[/QUOTE]

I'll give you more output if you need it!

---

### Post by eplemonster on 2008-12-29
I installed Wicd Manager and the wireless networks are available again, but for some reason I can't connect. It says "validating authentication" for 10 seconds then stops. I'm using dhcpcd as dhclient.

Please help!

---

### Post by eplemonster on 2008-12-29
I removed my WEP protection from my router and tried to connect to it, but I never obtained an IP.

---

### Post by ruchi on 2008-12-29
you should try to setup again your network setting.hope it will be helpful for you.

---

### Post by fx78 on 2008-12-29
I'm using the 4965AGN and had the same problem. Which seemed related to the fact that frequency used for wireless differ between US and Eu. If you live in Europe then this might solve your problems:

[http://ubuntuforums.org/showpost.php?p=6434998&postcount=119](http://ubuntuforums.org/showpost.php?p=6434998&postcount=119)

Reboot after updating, this solved my problems...

---

### Post by eplemonster on 2009-01-02
It still doesn't work. I can't connect to dhcpcd through the terminal. I tried blacklisting the native driver and installed ndiswrapper and modprobed it. Wicd ironically display all wireless networks except my own (router). The wlan card works perfectly in Windows and the connection is working fine, too. Please help. I sucks being stuck to Windows.

---

### Post by TadeoDiaz on 2009-01-05
I am having a similar problem. I have the same wireless card on a Lenovo 3000 V100 running Intrepid. My problem though is that I have connection issues at school. I am connecting at home to a D-link router with WEP encryption just fine but at school I can't seem to connect to a hidden wireless network without encryption unless I leave my laptop in suspend for a while first. I tried restarting several times and even suspending for up to 10 minutes but nothing.

Here is the output from terminal on sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:1a:44:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.0.105 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:0a:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:2a:7c:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 52:24:50:7e:95:01
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


I appreciate any help!

---

