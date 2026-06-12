---
title: "Ubuntu 10.04 rt3090 wireless keeps dropping"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by Mr Fahrenheit on 2012-03-27
I am a very new user of Linux after making the switch from windows after many years. So far I am very happy with making the switch. The only problem is my wireless which I have been having a number of issues with on my HP laptop. So far I have managed to get it "working" however now I am facing continuous disconnects. I am using the rt3090 wireless card. I have noticed that when it does disconnect the download speed is slowly reduced until eventually I am disconnected from the network, and have to restart network manager to get it back online. The disconnects vary largely, sometimes I have no issues for hours, other times it is every few minutes. I have tried pretty much all the tricks I could find on the net. I have also tried a number of different drivers. I am currently using the rt5390-dkms supplied by Marco. I have noticed that it is more stable then some of the previous drivers that I have used. 

Using ***lsm****od | grep rt ***I can see that the rt5390 module is listed.

```
rt5390sta            1364038  1 
cfg80211              148725  1 rt5390sta
parport                37160  2 ppdev,lp

```And ***sudo lshw -C network***:

 ```
 *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: e0:2a:82:5e:ff:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN ip=192.168.0.3 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:16 memory:c3400000-c340ffff

```As you can see my driver is listed as RALINK WLAN and not as rt5390, also when I view* connection information *using network manager the driver is listed as the rt2860. Even though it has been blacklisted, along with all the other ones.....:confused:

I have been at this for weeks now with no luck. 

Thanks in advance.

---

### Post by Mr Fahrenheit on 2012-03-27
Any Ideas?????

---

### Post by Mr Fahrenheit on 2012-03-28
Any ideas???

---

