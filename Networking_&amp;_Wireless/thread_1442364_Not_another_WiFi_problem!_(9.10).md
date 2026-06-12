---
title: "Not another WiFi problem! (9.10)"
date: 2010-03-29
forum: Networking &amp; Wireless
---

### Post by RileyRandom on 2010-03-29
I just can't seem to get this stupid wifi to work. I'm currently using Ethernet, so i have internet connection. I've already tried to install the drivers and such, and i tried to use that fwcutter, but with no luck.

---

### Post by Iowan on 2010-03-29
Does **sudo lshw -C network** reveal any new information?
(Post if possible)

---

### Post by RileyRandom on 2010-03-29
I'm just getting back into ubuntu after a break, and even back then i was a newbie at it, so i don't really know if what "anything new" would look like. But here is the results.


[B]  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b0:c1:ce
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.5 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:fe5fe000-fe5fffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:60:eb:73:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg [/B]

---

### Post by farbird on 2010-03-29
is the bcm4311 driver blacklisted?


probably u shd cut/paste the snippet from dmesg after the wifi is plugged in or enabled...

---

### Post by RileyRandom on 2010-03-29
> **farbird said:**
> is the bcm4311 driver blacklisted?


probably u shd cut/paste the snippet from dmesg after the wifi is plugged in or enabled...


Uhhh, a little help?;)

---

### Post by bkratz on 2010-03-30
> **RileyRandom said:**
> Uhhh, a little help?;)



Have you been here yet?

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by RileyRandom on 2010-03-30
The driver is activated and i have wireless enabled but there is no wireless connection under the wireless tab.

---

### Post by bkratz on 2010-03-30
> **RileyRandom said:**
> The driver is activated and i have wireless enabled but there is no wireless connection under the wireless tab.

If you drop to the terminal
Applications>>Accessories>>Terminal can you copy/paste the output here? 

```
sudo iwlist scan
iwconfig
rfkill list

```

---

### Post by RileyRandom on 2010-03-30
> **bkratz said:**
> If you drop to the terminal
Applications>>Accessories>>Terminal can you copy/paste the output here? 

```
sudo iwlist scan
iwconfig
rfkill list

```

Like so?


lo        Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:1F:90:E7:6E:D4
                    ESSID:"GXP21"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-59 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:1F:90:E0:33:47
                    ESSID:"YJHW7"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

eth0      Interface doesn't support scanning.

riley@riley-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
eth0      no wireless extensions.

riley@riley-laptop:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
riley@riley-laptop:~$

---

### Post by bkratz on 2010-03-30
> **RileyRandom said:**
> The driver is activated and i have wireless enabled but there is no wireless connection under the wireless tab.

Everything looks good in the last posting, which is your's and can you explain further what you mean in the above. If you right click on the neworking icon have you set up the required information. If you left click on the icon do you see both networks displayed?

---

### Post by RileyRandom on 2010-03-30
> **bkratz said:**
> Everything looks good in the last posting, which is your's and can you explain further what you mean in the above. If you right click on the neworking icon have you set up the required information. If you left click on the icon do you see both networks displayed?

OH MY GOD, after 3 days of trying all i had to do was right click on that icon, and not left click on it. I kept left clicking on it and going to edit connections. But soon as i right clicked on it, it showed my router. xD

---

### Post by bkratz on 2010-03-30
> **RileyRandom said:**
> OH MY GOD, after 3 days of trying all i had to do was right click on that icon, and not left click on it. I kept left clicking on it and going to edit connections. But soon as i right clicked on it, it showed my router. xD

But are you able to connect?

---

### Post by RileyRandom on 2010-03-30
Yes xD

---

### Post by bkratz on 2010-03-30
> **RileyRandom said:**
> Yes xD

Congratulations, you will find it worth the three days ( I spent 3 months!). Now please go to the thread tools above and select mark as solved, it may actually help someone else!

---

