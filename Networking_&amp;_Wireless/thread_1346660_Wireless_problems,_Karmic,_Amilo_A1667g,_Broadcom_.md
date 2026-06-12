---
title: "Wireless problems, Karmic, Amilo A1667g, Broadcom BCM4318...."
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by Euanbuntu on 2009-12-05
Hello all,

I've been having the archetypical Broadcom card problems when trying to get my wireless to function. I've looked through many of the other helpful replies to other Karmic users' requests for help but unfortunately I still cannot seem to get it to work.

So far I think I have the bcm43-fwcutter installed, but each time I try to use it from the terminal (am i meant to be fiddling with it that way in order for it to work? I think I am... :s ) the sole result is a complete loss of detection of any wireless capabilities. At the moment network manager is telling me wireless is disconnected.

Would some kind soul out there be willing to help me, and thus any other Fujitsu-Siemens Amilo A1667g users in setting up Karmic's wireless capabilities please?

euanbuntu
:-k

---

### Post by Euanbuntu on 2009-12-05
a few things I've managed to find whilst in the terminal:

root@scrattop:~# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:38:ea:b2
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e800(size=256) memory:febff400-febff4ff memory:febc0000-febdffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:febfc000-febfdfff
  [COLOR="Blue"][COLOR="Blue"][B]*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:90:4b:e6:90:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/B][/COLOR][/COLOR]

and

root@scrattop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:0987-6543-21
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So basically I think I'm asking how do I enable the disabled "**[COLOR="Blue"]*-network[/COLOR]**"?

---

### Post by uncaspi on 2009-12-05
Try to remove all lines except auto lo and iface lo inet loopback in /etc/network/interfaces and reboot. Se if the network icon shows up in the panel after rebooting. If you upgrade Karmic from an older version of Ubuntu it will still use the old conf files and that could cause problems

---

### Post by bkratz on 2009-12-05
> **Euanbuntu said:**
> a few things I've managed to find whilst in the terminal:

root@scrattop:~# lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:38:ea:b2
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:17 ioport:e800(size=256) memory:febff400-febff4ff memory:febc0000-febdffff(prefetchable)
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:febfc000-febfdfff
  [COLOR="Blue"][COLOR="Blue"][B]*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:90:4b:e6:90:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/B][/COLOR][/COLOR]

and

root@scrattop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:0987-6543-21
       **[COLOR="Red"]   Power Management:off[/COLOR]**
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

So basically I think I'm asking how do I enable the disabled "**[COLOR="Blue"]*-network[/COLOR]**"?



I may be wrong but doesn't this mean that there is switch to turn on  somewhere?

---

### Post by uncaspi on 2009-12-05
Network manager doesn't handle cards which are listed in /etc/network/interfaces and it shows a message when you click the network icon that the card is not handled or configured or something like that.
Maybe there is a switch somewhere. I never found it.

---

### Post by Euanbuntu on 2009-12-05
Thank you for your thoughts, uncapsi and bkratz. Please keep them coming if you can?

I should have mentioned that the icon is there and, if you are talking about a physical switch on the outside of the machine, then the switch is on; if you're talking about a virtual switch (i.e. a programmed one), then I have no idea. However, if you do mean the physical one then maybe this is a default message which is displayed because, as there is nothing which is actually controlling the card at the moment (not for long, I hope!!) then there is effectively no power management - once it has a driver, then maybe we might have power management too? Just a thought.

I'm not sure about this message which comes up when you click the icon - I just get a wee menu from a left click giving me the option under the heading of 'Wired Network' to click on 'Auto eth0' and another to disconnect from it. Also the wireless doesn't show up as selectable. What is shown, under 'Wireless networks' is 'wireless is disabled', under that is VPN Connections. Nothing more.

From a right click I can see the usual 'Enable networking', then a non-selectable option to 'Enable Wireless', then 'Connection information', 'Edit connections', and lastly 'About' - but like I say the option to 'Enable wireless' is not highlighted, not selectable.

Not sure if the above helps, but I hope so.

I really do want to get this machine working because it's been out of action for so long (on and off for most of this year in fact, and it's my only machine) due to one thing or another, so I seriously appreciate your help everyone. More importantly than that, your help lets me learn more about Ubuntu and Linux which is something I really want to do (maybe someone'll give me a 'linux for dummies' book this christmas? certainly, it's an apt title, and if no-one does get me one I'm certainly getting one for myself!)

---

### Post by Euanbuntu on 2009-12-06
> **uncaspi said:**
> Try to remove all lines except auto lo and iface lo inet loopback in /etc/network/interfaces and reboot. Se if the network icon shows up in the panel after rebooting. If you upgrade Karmic from an older version of Ubuntu it will still use the old conf files and that could cause problems

Just to let you know, this is a fresh install but I have been playing with it for two days now trying all sorts to get it going. I did install ndiswrapper, but completely removed it after I saw how complicated it was going to be.

I'm doing what you've suggested right now.

11.33am: the sole contents of /etc/network/interfaces is this:
"auto lo
iface lo inet loopback"

I didn't need to change anything, however it's still not working

---

