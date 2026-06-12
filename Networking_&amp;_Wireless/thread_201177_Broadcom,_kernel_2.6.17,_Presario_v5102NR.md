---
title: "Broadcom, kernel 2.6.17, Presario v5102NR"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by underdog on 2006-06-21
```

underdog@underdog-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device eth1 has been compiled with version 20
of Wireless Extension, while this program supports up to version 19.
Some things may be broken...

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

underdog@underdog-laptop:~$ sudo iwlist eth1 scan
Password:
Warning: Driver for device eth1 has been compiled with version 20
of Wireless Extension, while this program supports up to version 19.
Some things may be broken...

eth1      No scan results

```


I think this speaks for itself...what the heck is goin on?

---

### Post by Jayzilla on 2006-06-21
Have you tried:

```
sudo modprobe bcm43xx
```

That worked for me, at least.

---

