---
title: "networking restart problem"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by UT8F on 2010-06-21
Hi,
I got problem, when I try to restart network:

```
sudo /etc/init.d/networking restart
```

I got this:

```
ut8f@ut8f-laptop:~/Desktop$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"DLink"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:5A:52:A1:3F   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

Where is the problem?

---

### Post by UT8F on 2010-06-21
Fixed!
Edited:
```
/etc/network/interfaces
```

Added:
```
auto wlan0
iface wlan0 inet dhcp
```

And restarted network:
```
sudo /etc/init.d/networking restart
```

---

### Post by Iowan on 2010-06-21
Curious that sometimes the old ways still work...
Congrats!!!

---

