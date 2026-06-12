---
title: "Wireless Internet Access Drops intermittently Even when Network Connection is Active"
date: 2012-05-15
forum: Networking &amp; Wireless
---

### Post by bhopalino1 on 2012-05-15
Dear all,
I have a fresh install of Ubuntu 12.04 32bit on Thinkpad T400

Problem - Could able to connect to wireless connection without any issue and it works fine. But my internet access stops automatically every now and then. I could able to get back the access after few seconds when I keep of refreshing browser. 


Solution Tried - 
1) Set "Ipv6" to ignore in Wireless Internet settings -- No help
2) Set Wireless Power Management to "Off" -- No Help
3) Tried to use the option of disabling the "Wireless N" as suggested in this post  [http://ubuntuforums.org/showthread.php?t=1978457]("http://ubuntuforums.org/showthread.php?t=1978457")
This has reduced the frequency greatly but still on some occassion I see Internet access drop.

Any help would be appreciated.

---

### Post by squilookle on 2012-05-16
Hi bhopalino1 

Did you have the problems before you did your fresh install of 12.04? 

Can you tell us what wireless router and wireless card you are using? 

It sounds similar to issues I had with my wireless router, but there are many things that can go wrong (and many different wireless routers and cards) so it is quite possible it is an entirely different problem with similar results.

---

### Post by bhopalino1 on 2012-05-16
Before this I had Windows Vista on this machine and did not face this issue. 
Also with same network, I have another Win7 laptop and an Android tablet connected without any issues.

I am using cable modem+wireless gateway (both in same device) provided by my service provider.

When I run lspci command, I get following output. 

```
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
```

---

### Post by bhopalino1 on 2012-05-18
Friends,
I urgently need help from experts. I tried many solutions from internet but no help -- 

Problem -- 
Wireless connection drops now and then, but works fine after 2-3mins. Speed also varies sometime slow and sometime very good. 

**1 ) Machine Brand and Model (PC/Laptop):**
```
Lenovo Thinkpad T400
```

**2 ) Wireless Brand, Model and Wireless Chipset:**
```
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
```

**3) check interface:**
```
wlan0     IEEE 802.11abg  ESSID:"Indian"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1D:CF:8D:E4:20   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:729   Missed beacon:0

```

**4 ) Check for modules:**
```
iwlwifi               291847  0 
mac80211              436455  1 iwlwifi
cfg80211              178679  2 iwlwifi,mac80211

```

**5 ) Kernel boot messages :**
```
[    9.681088] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.681097] iwlwifi 0000:03:00.0: setting latency timer to 64
[    9.681117] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[    9.681119] iwlwifi 0000:03:00.0: pci_resource_base = f8984000
[    9.681121] iwlwifi 0000:03:00.0: HW Revision ID = 0x0
[    9.681203] iwlwifi 0000:03:00.0: irq 48 for MSI/MSI-X
[    9.681241] iwlwifi 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[    9.681300] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[    9.700498] iwlwifi 0000:03:00.0: device EEPROM VER=0x11e, CALIB=0x4
[    9.700501] iwlwifi 0000:03:00.0: Device SKU: 0Xf0
[    9.702543] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.867865] iwlwifi 0000:03:00.0: loaded firmware version 8.83.5.1 build 33692
[   10.680182] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   10.680563] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   10.797265] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[   10.797663] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[ 7978.117134] iwlwifi 0000:03:00.0: L1 Disabled; Enabling L0S
[ 7978.120138] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0

```

**6 ) Network configuration : **
```
*-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:68:11:9f:7e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:fc000000-fc01ffff memory:fc025000-fc025fff ioport:1840(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:65:3b:e1:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic-pae firmware=8.83.5.1 build 33692 ip=10.0.0.13 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:48 memory:f4300000-f4301fff

```

**7 ) Scan for networks:**
```
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:CF:8D:E4:20
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Indian"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003793a3016b
                    Extra: Last beacon: 30768ms ago
                    IE: Unknown: 0006496E6469616E
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0016FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010046127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10

eth0      Interface doesn't support scanning.

```

**8 ) Ubuntu Version: **
```
Description:	Ubuntu 12.04 LTS

```

**9 ) Kernel/architecture (including 32 vs. 64 bit): **
```
3.2.0-24-generic-pae i686
```

**10 ) Restarting the network:**
```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  
```

Any help would be highly appreciated....

---

### Post by Grouped on 2012-05-19
[http://vialki.ru/sforum/index.php?action=profile;u=192947](http://vialki.ru/sforum/index.php?action=profile;u=192947)

---

### Post by terabyte1 on 2012-05-19
It could be your ISP (the people who supply your phone/internet). This happens with me occasionally. Sometimes there are too many people on-line at any one time and the equipment relays temporarilly'drop' some internet lines to ease pressure. There again, as in my case, Our telephone company is busily installing fibre-optic cable in our region to get the area covered by the end of 2012 this can result in a disconection of the line due to line voltages being out of phase as they connect new equipment.


If the disconnection didn't happen before you re-installed Ubuntu/Kubuntu 12.04 there could be a problem with your grub - check this out. It's fairly easy to do and the Linux Format magazine has walk-throughs on how to check it out online, or failing this, try FullCircle Magazine (which is a free online computer magazine primarilly intended for Ubuntu/Kubuntu/xubuntu - but now covers several other flavours). Go to: [www.fullcirclemagazine.org](www.fullcirclemagazine.org) and the editor to whom you address  enquiries is the Editor Ronnie Tucker(ronnie@fullcirclemagazine.org) - hope that helps!:lolflag:

---

### Post by Rayaz on 2012-05-24
Waiting for a viable solution on a fresh install of 12.04 :(

---

### Post by jon zendatta on 2012-05-24
I have same problem on 12.04. Only started doing this last week

---

### Post by mattrock1988 on 2012-05-25
Guys... I am having the same issue as well! xD

I have a TP-LINK TL-WN722N which never had this problem before on other OSes. Then Ubuntu 12.04 LTS seems to cause these random page hangups which entail "cannot load" errors and the like. I then wait about a minute or so, click refresh, and then voila! The page springs back to life.

This is definitely not an issue with my router because I had used both PC-BSD 9 and Windows 8 on this network with zero issues. I wonder if there is something amiss with the network stack in this version of Ubuntu?

---

### Post by kevdog on 2012-05-25
Depending on how you guys upgraded to 12.04 -- did any of you try booting into a different kernel or possibly older kernel version?

---

### Post by buckbuzzo on 2012-05-25
I have the same issue using a DELL studio 1555 and an intel wifi Link 5100.
Internet works perfectly on my Windows 7 partition though.

I installed 11.10 just last month because I had it already on a memory stick. A couple days after installation, I was prompted to an automatic upgrade to 12.04, which I was happy to agree to. Until I found out about all the ensuing network issues.

I tried a few different things I could find here and there, but nothing made the trick so far. I haven't tried using another kernel; I actually would not know how to do this.

---

### Post by mattrock1988 on 2012-05-25
> **kevdog said:**
> Depending on how you guys upgraded to 12.04 -- did any of you try booting into a different kernel or possibly older kernel version?

Personally, I did a clean install to a freshly formatted JFS partition.

---

### Post by kevdog on 2012-05-25
Let me post -- I think its possible to downgrade kernel version without any dramatic results.  As you know -- it seems there is a kernel upgrade approximately every month if you are regularly doing updates.  It should be possible to actually "downgrade" rather than upgrade, however let me explore how to do this on a fresh install.

---

### Post by Erudhalion on 2012-05-26
I'm having the same problem on an HP Pavilion dv6-1040el, which has the same Intel card as the OP's. Except in my case I only have trouble when using my home network. All the other computers in my house work fine.
Disabling WIreless N seems (fingers crossed) to have fixed it.
I'll give it time and see what happens.
 
EDIT:It came back for a whole 5 minutes, but has now gone again.

---

### Post by buckbuzzo on 2012-05-26
I don't have the problem at work either, only with my home network. My ISP is xfinity, in case it makes a difference (?)

---

### Post by Erudhalion on 2012-05-26
> **kevdog said:**
> Depending on how you guys upgraded to 12.04 -- did any of you try booting into a different kernel or possibly older kernel version?

I upgraded from 11.10, so I tried to boot into the only other kernel Grub showed me (3.0.0-17-generic) but it didn't make any difference.

---

