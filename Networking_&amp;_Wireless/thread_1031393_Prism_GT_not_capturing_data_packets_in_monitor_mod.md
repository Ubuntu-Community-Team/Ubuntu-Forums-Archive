---
title: "Prism GT not capturing data packets in monitor mode"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by nitishd on 2009-01-05
wireless card :  Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

hey !
My wireless card isnt capturing data packets in monitor mode. I have tried with many sniffers like wireshark,kismet,airodump-ng but aint working . It is only capturing beacon frames broadcasted by AP's . 
I dont seem to figure out the reason fr it. Kismet takes it nicely into monitor mode but if I try to take it in monitor mode using airmon-ng it returns some error : 
sudo airmon-ng start wlan0


Interface	Chipset		Driver

wlan0			prism54pci - [phy0]/usr/sbin/airmon-ng: 833: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)

Please help me out. Thanks for your time.

---

### Post by nitishd on 2009-01-06
**Ubuntu hardy 8.04**
I am not using any explcitly compiled driver. 
Following is the result of lshw -C network : 
 description: Wireless interface
       product: **ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]**
       vendor: Intersil Corporation
       physical id: x
       bus info: xxxxxx
       logical name: wmaster0
       version: x
       serial: xxxxxx
       width: 32 bits
       clock: xxxxx
       capabilities: pm bus_master cap_list logical wireless
       configuration: broadcast=yes driver=prism54pci latency=32 maxlatency=28 mingnt=10 module=p54pci multicast=yes promiscuous=yes wireless=IEEE 802.11g

do I need to use any other driver fr it ? I was wary of using any other since this driver is working all fine(as in associating n all), except the problem m facing with the capture of data packets. But capturing is more important for my current project , so if any of you guys can suggest smthing .

---

