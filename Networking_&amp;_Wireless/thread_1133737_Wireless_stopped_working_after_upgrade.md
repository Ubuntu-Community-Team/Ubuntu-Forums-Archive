---
title: "Wireless stopped working after upgrade"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by arnaldo on 2009-04-23
Wireless used to work well with Intrepid, until about one month ago.  After a routine safe-upgrade, it stopped.  If I boot from the Intrepid CD, everything works well, Network Manager detects several networks in the neighborhood, and connects correctly to my home network.  On the other hand, in the regular installation, it shows no networks (of course, wireless is enabled).  Same happens at my workplace.

Two weeks ago I decided to stop trying on Intrepid and go for Jaunty.  Nothing new happened wrt wireless.  Here is some data that may be of some help.


1 ) Machine Brand and Model (PC/Laptop):

    Sony Vaio VGN-Z570AN

2 ) Wireless Brand, Model and Wireless Chipset:
Code:

$ lspci -nn
06:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]

3 ) check interface:

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:25:9c:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


$ iwconfig wlan0

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


4 ) Check for modules:

$ lsmod | grep iw

iwlagn                100228  0 
iwlcore                93184  1 iwlagn
led_class              12036  1 iwlcore
mac80211              217208  2 iwlagn,iwlcore
cfg80211               38032  3 iwlagn,iwlcore,mac80211

5 ) Kernel boot messages

$ dmesg | grep iw

[   15.253565] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   15.253568] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   15.253653] iwlagn 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.253682] iwlagn 0000:06:00.0: setting latency timer to 64
[   15.253745] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   15.275945] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   15.276013] iwlagn 0000:06:00.0: irq 2297 for MSI/MSI-X
[   15.276891] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.979130] iwlagn 0000:06:00.0: firmware: requesting iwlwifi-5000-1.ucode
[   18.303812] Registered led device: iwl-phy0:radio
[   18.303826] Registered led device: iwl-phy0:assoc
[   18.303842] Registered led device: iwl-phy0:RX
[   18.303854] Registered led device: iwl-phy0:TX

6 ) Network configuration

(Just the wireless part)
      description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:25:9c:04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  
7 ) Scan for networks:
Code:

$ iwlist scan

[Found 7 cells.  I am only interested in connecting to this one:]
         Cell 05 - Address: 00:1C:DF:CC:9A:A6
                    ESSID:"am-home"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=98/100  Signal level:-25 dBm  Noise level=-127 dBm
                    Encryption key:off
                    IE: Unknown: 0007616D2D686F6D65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000007a4fc5392b
                    Extra: Last beacon: 1316ms ago
 

8 ) Ubuntu Version:

$ lsb_release -d
Description:	Ubuntu 9.04

9 ) Kernel/architecture (including 32 vs. 64 bit):
$ uname -mr
2.6.28-11-generic i686

10 ) Restarting the network:

[eth0 part omitted]

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:21:5d:25:9c:04
Sending on   LPF/wlan0/00:21:5d:25:9c:04
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Evil Dax on 2009-04-23
Same problem here, using an Acer Aspire notebook.
First on Intrepid, and just now on clean install of Jaunty(64bit)

All seem to work, I can see 14 APs around me.
But it still crashes (as above) on getting a DHCP lease.

Already tried to load the backports:
```

sudo apt-get install linux-backports-modules-jaunty linux-backports-modules-jaunty-generic

```
of course, no luck.

Other tip:
```

sudo modprobe -r iwlagn && sudo modprobe iwlagn 11n_disable=1

```
did not do any good....

Any good tips would greatly be appreciated !

---

### Post by cpttripzz on 2009-04-24
I am having the same problem with this chipset and also with rt2570 in the 2.6.28 kernel, it works fine in .27, so until the kernel guys can figure it out I am staying with the old kernel

---

### Post by arnaldo on 2009-04-28
This is weird.  Booting from a fresh Jaunty CD, Network Manager works properly, but it is still a bust on my fuller system.

On the other hand, I just got wind of wicd; installed it and it seems to be working OK.

---

### Post by Muriluo on 2009-05-04
Same here on HP Pavilion tx1228ca. I updated Jaunty and it can´t see my wireless. 

[HTML]murilo@murilo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

murilo@murilo-laptop:~$ iwconfig wlan0
wlan0     No such device

murilo@murilo-laptop:~$ ifconfig wlan0
wlan0: error fetching interface information: Device not found
murilo@murilo-laptop:~$ 
[/HTML]

---

### Post by Muriluo on 2009-05-04
by the way, windows vista can´t see the wireless now... Nor Vista nor HP Network software...

---

### Post by Muriluo on 2009-05-04
so... it looks to be desabled. How do I eneble it?

[PHP]murilo@murilo-laptop:~$ sudo lshw -C network[/PHP]
 [PHP] *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:e9:03:1e:08:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes[/PHP]

---

