---
title: "Wireless interface disconnected, anyone know how to reconnect?"
date: 2010-12-18
forum: Networking &amp; Wireless
---

### Post by TMagic*04 on 2010-12-18
Hi,

I'm using the following wireless card:
```
  description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:24:21:4e:e6:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes promiscuous=yes wireless=802.11b/g
       resources: irq:17 ioport:b000(size=256) memory:dfc00000-dfc03fff

```

it was working previously and is still recognised with both ifconfig and iwconfig and I can bring it up and down etc.

however I can't scan for wireless networks and have problems using applications such as kismet so I ran nm-tool and this was my output:

```
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             disconnected
  Default:           no

```

does anyone know how I am able to reconnect it?

---

### Post by chili555 on 2010-12-18
> promiscuous=yesI wonder what that means. When you do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Is the behavior improved?

---

### Post by TMagic*04 on 2010-12-18
no there is no change in behaviour, infact under iwconfig before and after running the commands the mode specified was managed, so not sure why it's listed as promiscuous somewhere else....this was my output

```
wlan0     802.11b/g  Mode:Managed  Frequency=2.462 GHz  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

You have any idea what could be causing this?

---

### Post by bkratz on 2010-12-18
> **chili555 said:**
> I wonder what that means. When you do:```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed
sudo ifconfig wlan0 up
```Is the behavior improved?

@Chili

Found this old thread
[http://ubuntuforums.org/showthread.php?t=900916](http://ubuntuforums.org/showthread.php?t=900916)

Saying "
My understanding, is that when a networking device is in promiscuous mode (ifconfig device promisc), it should receive all packets whether the packet is directed to that device or not. With wired networking, the router/switch needs to be able to replicate all traffic to a single specified port (or if you're using a standard hub, since all traffic is indiscriminately anyway).

With wireless devices, since all the packets are broadcast anyway, a wireless device in promiscuous mode should pick up all wireless traffic on that SSID and channel, regardless of the target destination. 
"

Don't really understand the explanation though!

---

### Post by TMagic*04 on 2010-12-18
Ye that just seems to be an explanation of what promiscuous mode is, due to my work I often use it, however when I try to run something such as kismet which uses the card in promiscuous mode it wont start claiming problems with the interface.

I think the problem is due to it being listed as disconnected in nm-tools however i'm not sure how I can reconnect it...also when I run ifdown I get the following:

```
ifdown: interface wlan0 not configured

```

---

