---
title: "Intel Wifi Link 5100 / Lucid Lynx 10.04 LTS / Asus G50vt"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by Klink on 2010-05-22
It always worked under Linux Mint 8, but not at all under Lucid.
And yes, the wireless switch is on, but from what I'm seeing and what I've heard I think it might be a problem with RF_KILL.

> 03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100


> 
eth0      Link encap:Ethernet  HWaddr 00:23:54:6c:41:71  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe6c:4171/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1481490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:981018 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1903727734 (1.9 GB)  TX bytes:466491214 (466.4 MB)
          Interrupt:29 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2380 (2.3 KB)  TX bytes:2380 (2.3 KB)

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.


> iwlagn                121577  0 
iwlcore               124955  1 iwlagn
mac80211              238128  2 iwlagn,iwlcore
cfg80211              148386  3 iwlagn,iwlcore,mac80211


> [   11.200196] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   11.200199] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   11.200291] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.200319] iwlagn 0000:03:00.0: setting latency timer to 64
[   11.200409] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   11.244435] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   11.244523] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[ 9986.541645] iwlagn 0000:03:00.0: PCI INT A disabled
[ 9986.914165] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 9986.914168] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 9986.914236] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9986.914249] iwlagn 0000:03:00.0: setting latency timer to 64
[ 9986.914306] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[ 9986.962538] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 9986.962628] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[ 9998.576726] iwlagn 0000:03:00.0: RF_KILL bit toggled to enable radio.
[ 9998.629656] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[ 9998.677518] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[10007.317482] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
[10084.347883] iwlagn 0000:03:00.0: RF_KILL bit toggled to enable radio.
[10088.102006] iwlagn 0000:03:00.0: RF_KILL bit toggled to disable radio.
[10090.419874] iwlagn 0000:03:00.0: RF_KILL bit toggled to enable radio.


>   *-network DISABLED      
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:36:d3:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:fdffe000-fdffffff


> wlan0     Failed to read scan data : Network is down


> 2.6.32-22-generic x86_64


---

### Post by adamsiddhi on 2010-06-12
I too have the Intel(R) Wireless WiFi Link 5100 card. I just installed Lucid and can't get connected. 

I am a bit worried by the fact that the 5100 is not listed in the list of supported Intel WiFi cards:
[**[COLOR="Purple"]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI[/COLOR]**]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI")

Have you had any luck in getting it working?

---

### Post by derrickr on 2010-06-15
I was having exactly the same problem with my laptop (vaio vgn-sr19vn) fitted with the same Intel 5100 pci wifi, not being able to connect to my router.

I tried all of the suggested workarounds in this and various other forums / blogs, even going to the extreme of upgrading to the latest kernel (version 2.6.34 at time of writing).

To make it more frustrating, Network Manager saw the router but was having a problem authenticating (using wpa security). Also, everything still worked fine on the (dual-booting) Vista partition.

I spent nearly two days on this, but nothing worked.

I then remembered that I had a spare router, and thought I'd give it a try.

Within minutes I was back online :)

I was a little confused that Vista would connect OK, as all the hardware (router and laptop) was exactly the same. I'm therefore guessing my problem was caused by a mix of weaker signal from my old router and a Linux driver issue on my laptop.

I've seen quite a few threads regarding this type of issue, so I thought I'd feedback my solution in the hope that it may help someone else.

I'm also guessing that most people don't have a spare router lying around, but just in case they do, or maybe if they could borrow one, it might help to eliminate it from your fault-finding diagnosis.

Good luck!

---

### Post by adamsiddhi on 2010-06-15
i have solved my problem.

1. i was entering the wrong password for WPA & WPA2 Personal. I finally found the right one thank goodness.

2. after that it finally made a real connection. i was able to download fast via other internet apps but all my browsers were dead, could not make a full connection on many sites. switching to open ID was the solution for me. 

now i full speed connection. parting thought = i heard it time and time again from many ubuntu/linux users, the fact that getting started is very frustrating. if i was just a normal non technical consumer i would have given up on the first failure. and i have had failures in installing both Xubuntu and Ubuntu. I have spent several days getting my systems installed properly and getting connected to the net. I stuck to it because I am learning development in Ruby (which sucks in Windows) so it was a huge reason. no normal person would. and yeah... you hear frustrated users say "no wonder ubuntu/linux has such a small percent of the market, its so dam hard for most people to get started with out significant issue" i have heard that around only 10% of all people installing Lucid had no problem. the extra 90% were getting F-ed with failed installations and failed connections. 

Lucid was released WAY too early. Very embarrassing. Its like you have to go through a hazing to get on board with Ubuntu. still it is worth it for someone like me.

---

