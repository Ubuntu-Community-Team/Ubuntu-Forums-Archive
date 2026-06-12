---
title: "Another Cisco t30 wireless problem"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by shivers222 on 2011-09-02
Hi!

I have the same exact issues and results as the [original poster]("http://ubuntuforums.org/showthread.php?p=11213153") up to the last set of commands you asked him to do:

```
sudo iwlist eth1 scan cat /etc/network/interfaces dmesg | grep eth1
Here are my results to those commands:

hnk@HNK:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:25:9C:D1:67:8B
                    ESSID:"Wifi"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/100  Signal level=-60 dBm  Noise level:-102 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 2E:22:64:D6:EE:73
                    ESSID:"hpsetup"
                    Mode:Ad-Hoc
                    Frequency:2.437 GHz (Channel 6)
                    Quality=17/100  Signal level=-87 dBm  Noise level:-102 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=10

hnk@HNK:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1 
iface eth1 inet dhcp

auto wlan0
iface wlan0 inet dhcp
hnk@HNK:~$ dmesg | grep eth1
[   22.653330] airo(eth1): Firmware version 5.41.00
[   22.653335] airo(eth1): WPA supported.
[   22.653340] airo(eth1): MAC enabled 00:02:8a:fc:eb:27
[   33.488032] eth1: no IPv6 routers present
```



If you don't mind picking up where he left off, I would really appreciate the help. I have a IBM T40 with the exact same wireless card. It detects wireless networks but when I try to connect it just says Wireless disconnected.

Thanks a lot

---

### Post by nm_geo on 2011-09-02
Hi chili is away for a few days.

do... in terminal and paste results.

```
nm-tool 
```

Is the cell 1 Wifi your AP?  What kinda of security do you have on the wireless router?

---

### Post by Iowan on 2011-09-02
Moved your post to it's own thread, so that _when_ it's [SOLVED], you can mark it as such. ;)

---

