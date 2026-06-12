---
title: "Aircrack Help,"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by Dalek Draco ON LINUX on 2011-06-27
Hi

So I've installed aircrack-ng, and Im following this guide: [http://ubuntuforums.org/showthread.php?t=514723](http://ubuntuforums.org/showthread.php?t=514723)

I don't know what I'm doing wrong, but I can't find ath anywhere. I'm basically trying to penetration test our home network (our router is only WEP capable, so please don't suggest WPA as a solution). 

Output of lspci:
06:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

Output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"COSTERPC\xA0WIRELESS\xA0NETWORK"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:22:75:7A:54:97   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon0      IEEE 802.11abgn  Mode:Monitor  Frequency:2.452 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Output of lschw -c network:
 *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:8e:51:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.3 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:f0300000-f0301fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:9e:e9:a3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=jme driverversion=1.0.5 latency=0 multicast=yes
       resources: irq:37 memory:f0400000-f0403fff ioport:4400(size=128) ioport:4000(size=256)


Can someone please tell me a) if my wireless card is capable of doing the whole wep crack thing, and b) explain in relatively nooby terms (I can follow simple instructions :P) how I set up and run the program (I have aircrack-ng installed).

Thanks in advance

---

### Post by Dangertux on 2011-06-27
> **Dalek Draco ON LINUX said:**
> Hi

So I've installed aircrack-ng, and Im following this guide: [http://ubuntuforums.org/showthread.php?t=514723](http://ubuntuforums.org/showthread.php?t=514723)

I don't know what I'm doing wrong, but I can't find ath anywhere. I'm basically trying to penetration test our home network (our router is only WEP capable, so please don't suggest WPA as a solution). 

Output of lspci:
06:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection

Output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"COSTERPC\xA0WIRELESS\xA0NETWORK"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:22:75:7A:54:97   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

mon0      IEEE 802.11abgn  Mode:Monitor  Frequency:2.452 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Output of lschw -c network:
 *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:8e:51:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.3 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:f0300000-f0301fff
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:07:00.5
       logical name: eth0
       version: 03
       serial: 00:90:f5:9e:e9:a3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=jme driverversion=1.0.5 latency=0 multicast=yes
       resources: irq:37 memory:f0400000-f0403fff ioport:4400(size=128) ioport:4000(size=256)


Can someone please tell me a) if my wireless card is capable of doing the whole wep crack thing, and b) explain in relatively nooby terms (I can follow simple instructions :P) how I set up and run the program (I have aircrack-ng installed).

Thanks in advance

The long story short is this -- You are using WEP, your key can be cracked (and very quickly). That is a certainty. WEP cracking involves gathering IV's (Initial Vectors) , it is a mathematical certainty that once enough IV's are gathered, it will be cracked. Pass phrase randomization does not come into play until you get into WPA , which you said isn't an option so I won't elaborate.

As far as actually performing a basic WEP attack you can try this.

```

airmon-ng start wlan0 
airodump-ng -c 1 --bssid 00:00:00:00:00:00  -w wep mon0
aireplay-ng  -1 0 -a 00:00:00:00:00:00 -h 11:11:11:11:11:11 -e wepap  mon0
aircrack-ng -b 00:00:00:00:00:00  wep*.cap

```Where -c is the channel of the AP 00:00:00:00:00:00 is the MAC of the access point and 11:11:11:11:11:11 is your card's mac (or a spoofed mac) and wepap is the SSID of the AP. 

Alternatively you can do this at the aireplay-ng step

```

aireplay-ng -4 -b 00:00:00:00:00:00 -h 11:11:11:11:11:11 mon0

```I would opt for this option it's much faster then the above or the method mentioned in the tutorial.

Either way you will confirm that WEP is in fact deprecated. 

Have fun.

EDIT : This assumes you have injection capable wifi drivers if you don't see this link [http://www.aircrack-ng.org/doku.php?id=airdriver-ng](http://www.aircrack-ng.org/doku.php?id=airdriver-ng)

---

### Post by mikewhatever on 2011-06-27
> **Dalek Draco ON LINUX said:**
> Hi

So I've installed aircrack-ng, and Im following this guide: [http://ubuntuforums.org/showthread.php?t=514723](http://ubuntuforums.org/showthread.php?t=514723)

I don't know what I'm doing wrong, but I can't find ath anywhere.
```

Output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

**wlan0**     IEEE 802.11abgn  ESSID:"COSTERPC\xA0WIRELESS\xA0NETWORK"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:22:75:7A:54:97   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**mon0**      IEEE 802.11abgn  Mode:Monitor  Frequency:2.452 GHz  Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Output of lschw -c network:
 *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
**       logical name: wlan0**
       version: 00
       serial: 00:16:ea:8e:51:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless logical
       configuration: broadcast=yes driver=iwlagn ip=192.168.2.3 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:36 memory:f0300000-f0301fff

```


... and why do you look for 'ath0'? In your case, the logical name is **wlan0**, and when you start the card with airmon-ng, the **mon0** interface gets created.

This is one of those tutorials you can't just blindly follow, but need to understand.

---

