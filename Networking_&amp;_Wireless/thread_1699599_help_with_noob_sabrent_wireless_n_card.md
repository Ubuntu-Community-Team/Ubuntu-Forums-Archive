---
title: "help with noob sabrent wireless n card"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by gcomito11 on 2011-03-03
help just installed a pci wireless n card from sabrent, and cannot get it to run faster than 54mb/s
I am very computer illiterate but have been learning quickly since I found ubuntu 10.10

---

### Post by mikewhatever on 2011-03-03
What router do you use? Can it transfer faster then 54mbps? Are there other devices on the network (other computers, printers)?

---

### Post by gcomito11 on 2011-03-04
Yes it is a wireless n router supposedly transfer rates up to 300 mb/s I think it is a netgear.  It is about 5 feet away from the computer and one very flimsy wall in between. there are many other devices on the network, laptop ipad wii playstation 3.  the new card came with an instilation cd with linux files, I don't know if I need to install them, and if so how to install them?

---

### Post by mikewhatever on 2011-03-04
Can you post the output of the **sudo lshw -C network** command from a terminal window (Applications->Accessories). The output should show of the driver/card is capable of 11n transmission.

---

### Post by gcomito11 on 2011-03-04
> **mikewhatever said:**
> Can you post the output of the **sudo lshw -C network** command from a terminal window (Applications->Accessories). The output should show of the driver/card is capable of 11n transmission.
 
I will do that this evening thank you for your help mikewhatever, I am sure it is cabaple of n but we should check for sure, also if ubuntu drivers are not able to do n would this show the card as bing able to do n?  Nevermind I suppose we shall see when I get home.

---

### Post by gcomito11 on 2011-03-04
[QUOTE=mikewhatever;10521454]Can you post the output of the **sudo lshw -C network** command from a terminal window (Applications->Accessories). The output should show of the driver/card is capable of 11n transmission.

[/Q*-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: e0:cb:4e:c6:cb:8e
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:feac0000-feafffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:0d:0a:00:05:77
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-27-generic-pae firmware=N/A ip=192.168.1.135 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:febf0000-febfffff

---

### Post by mikewhatever on 2011-03-04
The output looks promising:
```
*-network
description: Wireless interface
product: RT2760 Wireless **802.11n** 1T/2R Cardbus
vendor: RaLink
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 00
serial: 00:0d:0a:00:05:77
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-27-generic-pae firmware=N/A ip=192.168.1.135 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE **802.11bgn**
resources: irq:16 memory:febf0000-febfffff
```

I've mentioned it before, but just to make sure, all devices on the network must support 11n. Is that the case?

---

### Post by gcomito11 on 2011-03-04
> **mikewhatever said:**
> The output looks promising:
```
*-network
description: Wireless interface
product: RT2760 Wireless **802.11n** 1T/2R Cardbus
vendor: RaLink
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
version: 00
serial: 00:0d:0a:00:05:77
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-27-generic-pae firmware=N/A ip=192.168.1.135 latency=64 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE **802.11bgn**
resources: irq:16 memory:febf0000-febfffff
```I've mentioned it before, but just to make sure, all devices on the network must support 11n. Is that the case?


That is a much more specific question than the previous one, I do not know does a nintendo wii, ps3 support wireless n?

I will quickly run the sudo network check on the laptop on the network and post the results if you can translate that for me.

---

### Post by gcomito11 on 2011-03-04
laptop on same network

*-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:25:54:f8
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:ef9fe000-ef9fffff


if I had to guess that would mean 802.11g is fastest we will see!

---

### Post by chili555 on 2011-03-04
I smell a rat.

Please run and post:```
lspci -nn
```Strip away everything that's not your Ralink. Also post:```
lsmod | grep rt2
```I believe your device is claimed, and conflicted, by two drivers; rt2800pci and rt2860sta. We may need to roll up our sleeves and blacklist.

---

### Post by gcomito11 on 2011-03-04
well 100 mb/s would be the slowest on the machines on the network unless for some odd reason a nintendo wii doesn't support faster than 100.

---

### Post by chili555 on 2011-03-04
> **gcomito11 said:**
> well 100 mb/s would be the slowest on the machines on the network unless for some odd reason a nintendo wii doesn't support faster than 100.Your post crossed mine; please see #10.

---

### Post by gcomito11 on 2011-03-04
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e20] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e23] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.5 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6 [8086:3a4a]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIB (ICH10) LPC Interface Controller [8086:3a18]
00:1f.2 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1 [8086:3a20]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
00:1f.5 IDE interface [0101]: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2 [8086:3a26]
01:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
03:00.0 Network controller [0280]: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus [1814:0701]
giannisdesk@giannisdesk-CM5571:~$ lsmod | grep rt2
rt2860sta             504703  0 
rt2800pci               8565  0 
rt2800lib              28961  1 rt2800pci
rt2x00usb               9779  1 rt2800lib
rt2x00pci               6029  1 rt2800pci
crc_ccitt               1351  2 rt2860sta,rt2800pci
rt2x00lib              27339  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               2633  1 rt2x00lib
mac80211              231959  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              144694  2 rt2x00lib,mac80211
eeprom_93cx6            1345  1 rt2800pci


I cannot wait till this stuff starts to make sense to me.

---

### Post by chili555 on 2011-03-04
> I cannot wait till this stuff starts to make sense to me.For reasons I don't even understand, two different drivers claim your device; sort of like two people trying to drive your car at the same time. Performance will not be ideal.> [COLOR="Red"]rt2860sta[/COLOR] 504703 0
[COLOR="RoyalBlue"]rt2800pci[/COLOR] 8565 0
rt2800lib 28961 1 rt2800pci
rt2x00usb 9779 1 rt2800lib
rt2x00pci 6029 1 rt2800pci
crc_ccitt 1351 2 rt2860sta,rt2800pci
rt2x00lib 27339 4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class 2633 1 rt2x00lib
mac80211 231959 3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211 144694 2 rt2x00lib,mac80211
eeprom_93cx6 1345 1 rt2800pci
We're going to blacklist the rt2800/rt2x00 suite in the hope that performance improves. I hope we will achieve N speeds. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the bottom:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot and tell us how your wireless is working.

---

### Post by gcomito11 on 2011-03-04
> **chili555 said:**
> For reasons I don't even understand, two different drivers claim your device; sort of like two people trying to drive your car at the same time. Performance will not be ideal.We're going to blacklist the rt2800/rt2x00 suite in the hope that performance improves. I hope we will achieve N speeds. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines at the bottom:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread carefully, save and close gedit.

Reboot and tell us how your wireless is working.



Done adn done, I have a whopping 54mb/s which is what we had on the desktop to start with.

---

### Post by chili555 on 2011-03-04
I did my best. I'm sorry I have no more suggestions.

---

### Post by gcomito11 on 2011-03-04
> **chili555 said:**
> I did my best. I'm sorry I have no more suggestions.

I certainly appreciate it and 56mb/s is more than I probably need perhaps if we blacklist the other of the two?
did you want me to reboot all the computers on the network or just this one?
also it was instantaneously 54 instead of starting at 1 and then moving up gradually like before so you have fixed one problem, and for that I thank you, and any oppourtunity to learn is also much appreciated
:guitar:

---

### Post by gcomito11 on 2011-03-04
most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib


is this what the last page was supposed to look like?

---

### Post by chili555 on 2011-03-04
> did you want me to reboot all the computers on the network or just this one?Just the one.

Does it respond to being forced?```
sudo iwconfig wlan0 rate 300M
iwconfig
```Did it stick?> perhaps if we blacklist the other of the two?You can certainly try it. My opinion is that the rt2800 suite is very weak, but you might have different luck. The only way to find out is to try it.

Edit the blacklist file as above, but make the additional lines look like:```
#blacklist rt2800pci
#blacklist rt2800lib
#blacklist rt2x00pci
#blacklist rt2x00lib
blacklist rt2860sta
```The pound sign # at the start of a line in a conf file means these lines are ***not*** to be read and acted on. That's called commenting out a line. Now do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2800pci
```Now is it working better?

---

### Post by gcomito11 on 2011-03-04
> **chili555 said:**
> Just the one.

Does it respond to being forced?```
sudo iwconfig wlan0 rate 300M
iwconfig
```Did it stick?You can certainly try it. My opinion is that the rt2800 suite is very weak, but you might have different luck. The only way to find out is to try it.

Edit the blacklist file as above, but make the additional lines look like:```
#blacklist rt2800pci
#blacklist rt2800lib
#blacklist rt2x00pci
#blacklist rt2x00lib
blacklist rt2860sta
```The pound sign # at the start of a line in a conf file means these lines are ***not*** to be read and acted on. That's called commenting out a line. Now do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2800pci
```Now is it working better?


I am illiterate as I said earlier, i cannot even figure out how to put those neat qupte boxes around parts of your previous thread.

the first part reads like this

giannisdesk@giannisdesk-CM5571:~$ sudo iwconfig wlan0 rate 300M
giannisdesk@giannisdesk-CM5571:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"giannishousesecured"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: C0:3F:0E:8F:68:EC   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-40 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by gcomito11 on 2011-03-04
> **chili555 said:**
> Just the one.

Does it respond to being forced?```
sudo iwconfig wlan0 rate 300M
iwconfig
```Did it stick?You can certainly try it. My opinion is that the rt2800 suite is very weak, but you might have different luck. The only way to find out is to try it.

Edit the blacklist file as above, but make the additional lines look like:```
#blacklist rt2800pci
#blacklist rt2800lib
#blacklist rt2x00pci
#blacklist rt2x00lib
blacklist rt2860sta
```The pound sign # at the start of a line in a conf file means these lines are ***not*** to be read and acted on. That's called commenting out a line. Now do:```
sudo rmmod -f rt2860sta
sudo modprobe rt2800pci
```Now is it working better?

Changed the blacklists then did the sudo's here is what happened


giannisdesk@giannisdesk-CM5571:~$ sudo rmmod -f rt2860sta
ERROR: Removing 'rt2860sta': Resource temporarily unavailable
giannisdesk@giannisdesk-CM5571:~$ sudo modprobe rt2800pci
giannisdesk@giannisdesk-CM5571:~$ 

if i go to my connection information it is using the driver 2860sta

---

### Post by gcomito11 on 2011-03-04
Thanks for all your help I am an extreme noob and really appreciate it.

---

### Post by chili555 on 2011-03-04
> giannisdesk@giannisdesk-CM5571:~$ sudo rmmod -f rt2860sta
ERROR: Removing 'rt2860sta': Resource temporarily unavailableYou probably need to take the interface down first:```
sudo ifconfig wlan0 down
sudo rmmod -f rt2860sta
sudo modprobe rt2800pci
sudo ifconfig wlan0 up
```Or...reboot.

---

### Post by gcomito11 on 2011-03-04
> **chili555 said:**
> You probably need to take the interface down first:```
sudo ifconfig wlan0 down
sudo rmmod -f rt2860sta
sudo modprobe rt2800pci
sudo ifconfig wlan0 up
```Or...reboot.

well I am satisfyingly confused now, I couldn't get 
sudo ifconfig wlan0 up

to work so I had to reboot and started at 1mb.s and now am back at 54 and the driver
driver is 2800?

what are your thoughts

---

### Post by gcomito11 on 2011-03-04
u know what is really impressive it is that i can only assume you are working on like ten other thing right now and my wife is looking at me like I am crazy cause this computer and this one thing is going to consume my entire world for a weekend lol.

---

### Post by gcomito11 on 2011-03-04
I think at teh bare minimum we should go back to what we had when the driver was 2860 that one stayed at 54 without fluctuation

---

### Post by chili555 on 2011-03-04
> u know what is really impressive it is that i can only assume you are working on like ten other thing right nowIt's only ten if you include watching TV and reading another forum about cars and emailing my daughter...> what are your thoughts I'd go back to rt2860sta.```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
**#**blacklist rt2860sta
```Content yourself that this driver and this card may not do N speeds. You might email the author:```
$ modinfo rt2860sta 
filename:       /lib/modules/2.6.35-27-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         [COLOR="Red"]Jett Chen <jett_chen@ralinktech.com>[/COLOR]
firmware:       rt3090.bin
firmware:       rt2860.bin

```He might answer.

---

### Post by gcomito11 on 2011-03-04
I would include those things as all i can do is wait with baited breath for your response and drink a brew... ohh and breathe, I always forget to remember to breathe.
thanks for doing your best chills I will never forget your lesson about shift 3 button on a blacklist!

ps I emailed creator as you suggested but I think I may be below his level of worry.  That would probably be like THOR worrying if a rock is upset today or not.

---

### Post by chili555 on 2011-03-04
Getting N speeds is a common problem with some drivers including Ralink. Keep us posted about your progress. The searchers and I will be interested in the result.

---

