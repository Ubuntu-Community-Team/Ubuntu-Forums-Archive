---
title: "can't connect to linksysE2000 router"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by greyoracle on 2013-03-07
I used to be able to connect to my router and now I can't for some reason; it happened all of a sudden.  I'm not sure what relevant information to include except that I can still connect to the router via a dual boot to Windows 7 and I can connect via Ubuntu to at least one other wireless router of someone in my neighborhood.  It probably doesn't help that I'm running a proprietary driver (Broadcom STA wireless driver) to make things work, so I'm not sure what anyone will be able to do here, but any help would be appreciated.  Thanks.

---

### Post by Bucky Ball on 2013-03-07
*Thread moved to **Networking & Wireless***

You might have better luck here and you could start with providing the output of these two commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by greyoracle on 2013-03-07
```
sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:1f:46:4f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k firmware=0.12-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:e9600000-e961ffff memory:e9680000-e9680fff ioport:8040(size=32)
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 1c:65:9d:9b:c1:1e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) ip=192.168.1.107 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:e6e00000-e6e03fff


```
iwconfig
```
Command 'iwconfig' is available in '/sbin/iwconfig'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
iwconfig: command not found

```
sudo iwconfig
```
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:B8:6B:8B   
          Bit Rate=1 Mb/s   Tx-Power=200 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=23/70  Signal level=-87 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by Bucky Ball on 2013-03-08
Ouch. That is pretty much unreadable. What happened? Please copy from the terminal and paste. Edit post three to paste the outputs and use [code] tags (you can add manually or 'Go Advanced', mark code and hit the # icon.

---

### Post by greyoracle on 2013-03-10
sorry I'm on a very slow connection and was under some time pressure when I first posted #3.  I think it's much more readable now.  thanks for your patience.

---

### Post by greyoracle on 2013-03-17
Hi, it's been a week and I haven't heard from you.  I was just wondering if there was something else that I needed to do first.  thanks.

---

### Post by greyoracle on 2013-04-12
It turns out that if you remove the proprietary Broadcom STA wireless driver everything works (ie I can connect to routers that require a password when before I could only connect to unsecured routers).  not that anyone much cares at this point :p  Even I gave up on this thread

---

