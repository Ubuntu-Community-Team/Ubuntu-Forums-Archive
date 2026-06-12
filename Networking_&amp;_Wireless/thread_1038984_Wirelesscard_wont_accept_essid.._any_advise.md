---
title: "Wirelesscard wont accept essid.. any advise?"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by kzm. on 2009-01-14
Hey.

I have a really weird problem I can not find any answer to it, may be somebody can point me into some direction. 

My router is open and unprotected. Wirelesscard is actually "optimized" (if you believe the manufacture) for the router. The wirelesscard seems to run fine and still every time i try to set the essid nothing happens, no error, no assignment. Setting essid worked on my old router and card.

```
lshw -C network
 *-network:1
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: a
       bus info: pci@05:0a.0
       logical name: ra0
       version: 00
       serial: 00:0c:f6:3e:e1:c0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 multicast=yes wireless=RT2860 Wireless
       resources: iomemory:fc510000-fc51ffff irq:201
```

"iwlist ra0 scan" works in the sense it shows my router next to the million others in reach.

```
sudo iwconfig ra0 essid "whatever"

sudo iwconfig ra0 
ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.442 GHz  Access Point: Not-Associated   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:-256 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Anywhere else to look at if something is going wrong?

P.S.: I actually already posted this problem under a different thread, I am sorry if this is bad behavior, but I wonder if nobody reacted because it is actually out of the scope of the thread:  [[all variants] Walkthrough - Installing Ralink 2860 Based Wireless Adapters]("http://ubuntuforums.org/showthread.php?t=966185")

---

### Post by wmdiem on 2009-01-14
```
iwlist scan 
```
should give you an AP hex address
try setting that with 
```
iwconfig ra0 ap <insertaddress>
```
This is all from memory so if it doesn't work, you might want to use the help or manpage for syntax.
Also you may want to manually set, in the same way, the frequency, channel, and mode (if the ap is "master" set your computer to "managed"). Theoretically you can do all this in one iwconfig command, but one usually gets better results setting them individually. Also, results tend to be best bringing the interface down (ifconfig) before setting them, then bringing it back.

---

### Post by kzm. on 2009-01-14
Ah!! sweet! thank you so much!!!!!!!!!

:popcorn:

now i only have to get the wpa part working...not sure why it isnt. ](*,)

---

