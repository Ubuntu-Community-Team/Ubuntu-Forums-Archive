---
title: "Support requested for Atheros AR242x 802.11abg Wireless PCI Express Adapter"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by dneril on 2008-12-23
Hi all.  I'm working off of Ubuntu v8.10, on a Toshiba Satellite a135 laptop.  I've searched through the forums looking for previously-posted solutions, but I haven't had any luck, so I'm posting this as a new thread.

I've tried to work with **madwifi** and **ndiswrapper**, but to no avail (mostly just by following instructions posted on other threads).

Results of **lspci**:
```
02:00.0 Ethernet controller: **Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter** (rev 01)

```

Results of **ifconfig**:
```
wlan0     Link encap:Ethernet  HWaddr 00:19:7d:ca:34:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7D-CA-34-A5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Results of **iwconfig**:
```
wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Results of **lshw -C Network**:
```
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7d:ca:34:a5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

I have a couple of proprietary drivers installed and in use also.  I've tried deactivating them, also with no result.  They are:
"Support for 5xxx series of Atheros 802.11 wireless LAN cards" and
"Support Atheros 802.11 wireless LAN cards"

Don't really know why I have two on there.  When I began trying to get my wireless connection to work there was only one.

I hope this isn't information overload!  I hope someone out there can help me.

---

### Post by dneril on 2008-12-23
I think this might also help:

Results of **dmesg**:
```
[   33.095635] wlan0: authenticate with AP 00:14:bf:08:b8:70
[   33.097602] wlan0: authenticated
[   33.097613] wlan0: associate with AP 00:14:bf:08:b8:70
[   33.099674] wlan0: RX AssocResp from 00:14:bf:08:b8:70 (capab=0x401 status=0 aid=6)
[   33.099682] wlan0: associated
[   33.101175] wlan0: **disassociating by local choice (reason=3)**
[  101.051269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2939.834593] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2943.810543] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2944.920756] wlan0: authenticate with AP 00:14:bf:08:b8:70
[ 2944.922306] wlan0: authenticated
[ 2944.922317] wlan0: associate with AP 00:14:bf:08:b8:70
[ 2944.924358] wlan0: RX AssocResp from 00:14:bf:08:b8:70 (capab=0x401 status=0 aid=6)
[ 2944.924366] wlan0: associated
[ 2944.925432] wlan0: **disassociating by local choice (reason=3)**

```

It looks like my wlan0 is "disassociating by local choice"?  Could this be the problem?

Also:
Results of **iwlist scan**:
```
wlan0     No scan results

```

Results of **uname -mr**:
```
2.6.27-9-generic i686

```

---

### Post by superprash2003 on 2008-12-23
post output of iwlist scanning from the terminal

---

### Post by dneril on 2008-12-24
```
dneril@dneril-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```

Also - I updated the first post with info for wmaster0.  I thought this might have something to do with the problem; since **lshw -C Network** is showing wmaster0 as the logical name for my Atheros wireless card.

I'm checking through your tech tutorial, superprash, to see if that will be able to solve my problem.

Edit: Yup, tried following it, step by step; but it didn't change anything.  Help!

---

### Post by superprash2003 on 2008-12-24
your output says that you dont have wireless networks around you.. wlan0 searched but couldnt find any!!do you have any hidden wifi networks?

---

### Post by dneril on 2008-12-24
I think that there is one unsecured wireless connection in my area - which is called linksys.  There are several password-protected wireless networks, one of which is mine.  I can connect to both linksys and my own wireless network when I load XP.  Is there a different procedure for connecting to a secured wireless network?

---

### Post by dneril on 2008-12-26
Bump - and merry christmas Ubuntuans!

---

