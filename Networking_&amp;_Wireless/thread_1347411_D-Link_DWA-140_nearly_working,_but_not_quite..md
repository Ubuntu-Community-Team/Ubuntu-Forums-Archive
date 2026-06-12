---
title: "D-Link DWA-140 nearly working, but not quite."
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by davemar on 2009-12-06
I'm trying to get my D-Link DWA-140 wireless USB stick working on my laptop running 8.04, but with no joy. I installed the ralink rt2870 drivers and they seem to be doing the right thing.

If I do ifconfig I get (of interest):
```
ra0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx
           inet6 addr: xxxx:xxxx:xxxx:xxxx:xxxx/xx Scope:Link
           ..etc

ra0:avahi       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx
           inet addr:xxx:xxx:xxx:xxx ...etc

```

If I do "iwconfig ra0" I get:
```
ra0     Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
        Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
        Bit Rate:1 Mb/s
        RTS thr:off  Fragment thr:off
        Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
        ...etc (parameter with value 0).

```

and if I do "iwlist scan" I get lots of cells coming up under ra0 including in Cell 02 my wireless router:
```
Cell 02 - Address xx:xx:xx:xx:xx:xx
       Protocal:802.11g
       ESSID:"NETGEAR"
       Frequency:2.462 GHz (Channel 11)
       Quality:100/100 Signal Level:-25 dBm  Noise level:-92 dBm
       Encryption key:on
       Bit Rates:54 Mb/s

```

So clearly the device is working and picking up my router, but I can't seem to get it to use it as the network connection using "Network Settings" in the admin menu. I've entered the ESSID, WEP key, etc, but can't ping anything in the outside world. 

How do I get ra0 set up to point to Cell 02, and how do I get ra0 to be the network connection of use?

Sorry about the cut-down screen quotes, I'm copying by hand from the laptop screen to my internet connected desktop!

---

