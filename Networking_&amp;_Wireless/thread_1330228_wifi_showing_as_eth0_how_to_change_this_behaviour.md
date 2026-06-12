---
title: "wifi showing as eth0 how to change this behaviour"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by tapas_mishra on 2009-11-18
My Wifi card is showing as eth1
```

root@tapas-laptop:~# cat /proc/net/wireless 
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
  eth1: 0000    5.  -56.  -91.       0      1      0      0      0        0

```
and 
```

root@tapas-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"Airtel"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:5E:11:4E:0C   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=4/5  Signal level=-58 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

How can I see it as wlan0 normal connections

---

### Post by chili555 on 2009-11-18
> How can I see it as wlan0 normal connectionsIs wlan0 'normal'? I have a laptop using the ipw2200 driver that uses the eth1 interface and another that uses iwl3945 and uses wlan0. My old prism2 card uses eth1. Other wireless devices use ra0, ath0, etc. I believe the interface name is embedded in the driver. It will therefor be *very* difficult to change.

I would not be dismayed with eth1 for a wireless interface. I have one and it works perfectly.

---

### Post by Iowan on 2009-11-18
> **chili555 said:**
> I would not be dismayed with eth1 for a wireless interface. I have one and it works perfectly.My laptop also calls wireless interface eth1. 

Dunno if an edit to* /etc/udev/rules.d/70-persistent-net.rules* would help, if it would stay edited, or if it would just complicate things elsewhere.

---

