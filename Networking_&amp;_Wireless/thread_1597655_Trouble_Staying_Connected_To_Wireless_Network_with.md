---
title: "Trouble Staying Connected To Wireless Network with Multiple Access Points"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by silverhammermba on 2010-10-15
I can connect to my school's wireless network using the standard network manager, but often (not always) it repeatedly disconnects and reconnects every few minutes. Occasionally it also prompts me for the security information again (even after it previously connected successfully).

By running iwconfig when it's on the fritz, I can see that it's often switching access points for the network - which is what I think is causing the problem. It disconnects and reconnects even when the signal strength for the current AP is fine, and it will often switch to an AP with a weaker signal strength.

$sudo lshw -C network
```
description: Wireless interface
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:05:00.0
logical name: wlan0
version: 10
serial: 74:f0:6d:27:45:cb
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 ip=128.180.52.228 latency=0 link=yes multicast=yes wireless=802.11bg
resources: irq:16 ioport:2000(size=256) memory:f0100000-f0103fff
```

$iwlist scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:7A:AB:BA:30
                    ESSID:"lu"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:1
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=68/100  Signal level=-69 dBm  Noise level=-104 dBm
                    Extra: Last beacon: 18ms ago
```

---

### Post by silverhammermba on 2010-10-21
Bump, because this problem is annoying the hell out of me.

After a little more examination of the problem, I've noticed that often my internet connection will stop working long before Ubuntu actually says I'm disconnected from the network. When it's disconnecting and reconnecting really frequently, the connection will stop working very soon after connecting - sometimes only about a minute afterwards - but will then go for several minutes where it will say I'm connected when I'm actually not.

Also, when connecting to the network on Windows or OSX, the user has to accept a verisign certificate from the network before connecting. No such thing happens in Ubuntu, could that be contributing to the problem?

---

### Post by hellmitre on 2011-01-27
I've noticed the same thing with several other machines with Realtek cards, both Windows and Linux (though it seems to be worse on Linux). The only thing that's helped for me has been to manually associate with one access point via
```
iwconfig wlan0 scan
``` and looking for the MAC address of the access point with the best signal. Then ```
iwconfig wlan0 ap *access point mac here*
``` Then 
```
iwconfig wlan0 essid *network name* && dhclient wlan0
```.

Hope this helps.

---

### Post by siwelchungster on 2011-04-05
Don't mean to revive a few month old thread, but it should be
```
sudo iwlist scan
```
This wireless problem has still been an issue ever since maverick. I'm running ubuntu natty beta 1, and the issue still exists. connection frequently dropping and not displaying the correct status when in the range of multiple access points (eg. university campus)

---

### Post by ZTiger on 2011-09-07
I have same issue. Some days will be better than others but ultimately I have between six and eight access points that my system will see in the one network. I've used iwevent to watch and see what is happening. 

Some times the card will go between two access points with no problem. However occasionally it will fail to establish a connection with the new AP and it may take several cycles before it re-establishes a connections.

I notice this issue only in places where their are multiple AP's for the same wireless network. At home it has no problem maintaining a connection to my home wireless. 

Also not that this seems to only be an issue with WAP. We have another open network with multiple AP's and there doesn't seem to be a problem maintaining a connection. Windows and Mac systems have no issue in the environment.


System Information
Dell E6420 with Intel Centrino Advanced-N 6205 wireless card.
Ubuntu Natty 11.04 - 32 Bit

---

