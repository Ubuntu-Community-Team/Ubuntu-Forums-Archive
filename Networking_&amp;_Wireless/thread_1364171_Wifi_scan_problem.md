---
title: "Wifi scan problem"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by Zakhafr on 2009-12-25
Hi,

I have a problem connecting to my AP as it is NOT scanned on one of my installations.

Both installations run Karmic :
**:~$ cat /etc/lsb-release**
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```

The dongle is a RTL8187L, it works fine.
**:~$ lsusb**
```
Bus 001 Device 108: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
```

The wifi stack looks ok:
**:~$ lsmod**
```
Module                  Size  Used by
(...)
rtl8187                53604  0 
mac80211              209912  1 rtl8187
led_class               5256  1 rtl8187
eeprom_93cx6            2528  1 rtl8187
cfg80211              109144  2 rtl8187,mac80211
(...)
```

When I ask for frequencies capabilities I get the whole range (1 to 13) on both installations:
[b]:~$ sudo iwlist wlan5 freq
[/b]```
wlan5     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.412 GHz (Channel 1)
```

But when I scan, I get different results, and especially a lack of channels 1 & 2 on one of my installations.

Scan that works:
**:~$ sudo iwlist wlan5 scan | grep 'Channel:'**
```
                    Channel:1
                    Channel:4
                    Channel:1
                    Channel:1
                    Channel:1
                    Channel:1
                    Channel:3
                    Channel:4
                    Channel:4
                    Channel:4
                    Channel:6
                    Channel:6
                    Channel:10
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:10
                    Channel:13
                    Channel:13
                    Channel:13
                    Channel:13
                    Channel:1
                    Channel:1
                    Channel:6
                    Channel:4
                    Channel:10
                    Channel:13
                    Channel:1
                    Channel:1
                    Channel:1
                    Channel:3
                    Channel:4
                    Channel:6
                    Channel:6
                    Channel:6
                    Channel:7
                    Channel:1
                    Channel:1
                    Channel:1
                    Channel:1
                    Channel:1
                    Channel:4
                    Channel:6
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:10
```

Scan that DOES NOT works:
**:~$ sudo iwlist wlan5 scan | grep 'Channel:'**
```
Channel:3
                    Channel:3
                    Channel:3
                    Channel:6
                    Channel:6
                    Channel:6
                    Channel:6
                    Channel:6
                    Channel:6
                    Channel:6
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:7
                    Channel:11
                    Channel:10
                    Channel:11
                    Channel:10
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:9
                    Channel:9
                    Channel:9
                    Channel:9
                    Channel:9
                    Channel:11
                    Channel:11
                    Channel:10
                    Channel:11
                    Channel:13
                    Channel:13
                    Channel:13
                    Channel:11
                    Channel:13
                    Channel:13
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:11
                    Channel:13
                    Channel:13
                    Channel:13
```

As you can see, on the first scan there are some AP on channel 1.
On the second scan, no matter how many times I try to repeat the scan, I get absolutely nothing from channel 1.

Of course the Wifi device is an external dongle, and it is in the exact same place on both scans. I just unplugged it from PC 1, and plugged it to PC 2.

The dongle works fine (even on channel 1) on the first PC.
On the PC where it won't scan, I have no trouble getting AP on channel 1 if I use airmon-ng.

It would have missed channels 12 and 13, I would have guessed a "region" problem, as 12 and 13 are authorized from where I am (Europe) but not in other regions (US).


But not scanning channel 1 is quite inexplicable for me!

Anyone could give ideas why it is so, and how to fix it?

(Apparently it does the same bug with NetworkManager as I don't see my AP which is on channel 1 on the faulty PC, and it works fine on the other PC)

---

### Post by Zakhafr on 2009-12-26
Any idea on this strange bug ? ):P

---

### Post by Zakhafr on 2009-12-29
No one has a clue why my Wifi dongle won't scan channel 1 ? :(

---

