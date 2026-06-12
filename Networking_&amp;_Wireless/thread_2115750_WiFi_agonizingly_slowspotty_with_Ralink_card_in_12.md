---
title: "WiFi agonizingly slow/spotty with Ralink card in 12.10"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by the2ndgenesis on 2013-02-13
Hey guys. The title of this thread pretty much says it all, I've been having some major wireless issues on the Quantal partition of my newly built PC. Since I don't have an Ethernet jack where my PC currently resides I've been using a [**_Rosewill RNX-N300X wireless card_**]("http://www.rosewill.com/products/1465/ProductDetail_Overview.htm") with a Ralink RT2860T chipset.

The card seems to work fine in my Windows partition and it works well ~75% of the time in Quantal, but the rest of the time it's frustratingly unreliable. It seems to drop the connection or throttle it to an insufferable speed even though the Network Manager maintains that I'm still on the network while it's doing that. It generally stays that way for as long as a minute or more before going back to normal and as far as I can tell it's completely arbitrary when it happens; I can't seem to reproduce it with any consistency.

I've spent hours trying to diagnose the nature of the problem- based on a [_**previous thread**_]("http://ubuntuforums.org/showthread.php?t=1794360") I'm inclined to say it might be a competing driver issue- but before I go diving into configuration files I wanted to stop by here to ask people who actually know what they're doing. Here are some outputs for context's sake:

```
sudo lshw -c network
```
```

[...]
*-network
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: Ralink corp.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: wlan0
       version: 00
       serial: 68:1c:a2:04:1f:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.5.0-23-generic firmware=0.34 ip=192.168.1.108 latency=32 link=yes maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f7200000-f720ffff

```


```
lsmod | grep rt2
```
```
rt2800pci              18529  0 
rt2800lib              58731  1 rt2800pci
crc_ccitt              12708  1 rt2800lib
rt2x00pci              14476  1 rt2800pci
rt2x00lib              54939  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539958  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              206797  2 rt2x00lib,mac80211
eeprom_93cx6           13345  1 rt2800pci

```


```
iwconfig
```
```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"x"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: x
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1867  Invalid misc:31   Missed beacon:0

```

Anyone have any ideas? I'm willing to try anything at this point, this is pretty much the only thing that's been difficult for me with this current install. Thanks everyone!

[Edit: In retrospect I should have consulted this subforum before picking this card, as it doesn't seem to be mentioned in the sticky about supported PCI cards. My mistake!]

---

### Post by the2ndgenesis on 2013-02-13
And yes, I've tried to install the [tarball driver]("http://www.rosewill.com/Mgnt/Uploads2/AttachmentForProduct/rnx-n300x_linux_v2.4.0.0.tar") mentioned on the product website but I can't seem to even get ./configure to run; it doesn't help that the readme file is rather poorly written and hard to follow.

---

