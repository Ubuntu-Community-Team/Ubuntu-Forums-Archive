---
title: "Server 11.04 wireless, AP not associated"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by grunthus on 2011-05-10
Hi, on a fresh install of 11.04 server edition, my Atheros AR5001X+ wireless card is working, and I can see the wireless carrier: iwscan provides this:

```
          Cell 02 - Address: removed
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:off
                    ESSID:"removed"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000088144e4977
                    Extra: Last beacon: 2792ms ago
                    IE: Unknown: 00085349434755455354

```I can run
```
sudo iwconfig wlan0 essid REMOVED key open mode managed ap REMOVED
```After which iwconfig shows:
```
wlan0     IEEE 802.11abg  ESSID:"REMOVED"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```I'm clearly missing a step to get the AP associated. Works straight away with desktop edition running network manager on same hardware.

Any ideas? Thanks

/etc/network/interfaces:
```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```

---

### Post by chili555 on 2011-05-10
> auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcpPlease try this:```
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid removed
```Then do:```
sudo ifdown wlan0 && sudo ifup wlan0
```Does it connect?> Quality=[COLOR="Red"]23[/COLOR]/70 This might be an issue.

---

### Post by grunthus on 2011-05-16
Hi, thanks for replying. Was away from server, so first chance to try today! 
Tried adding wireless-essid to interface file and ifdown/up. No joy.

The strength of the signal is low, however the same machine connects straight away using ubuntu desktop edition with network manager.

Still showing AP not associated. Any other ideas before I go back to desktop edition?

Cheers

Chris

---

### Post by chili555 on 2011-05-16
What does this tell us?```
sudo cat /var/log/syslog Grep wlan
```If this is long, just post the 10-15 lines that illustrate an attempt to connect. Also post:```
ps aux | grep -i network
```

---

### Post by grunthus on 2011-06-07
Hi, thanks for your help. After some alterations to the interfaces file and ifdown/ifup, the AP was associated. As you suspected, the connection strength was a factor in my difficulties.

Thanks

Chris

---

