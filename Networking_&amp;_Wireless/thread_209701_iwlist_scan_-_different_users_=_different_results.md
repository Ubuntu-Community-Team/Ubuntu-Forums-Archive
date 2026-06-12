---
title: "iwlist scan - different users = different results"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by gabe-kai on 2006-07-05
Hi Everyone,

I've just installed Ubuntu 6.06 on a Dell Inspiron 1150 laptop, which uses a Broadcom BCM4306 (1350 WLAN Mini-PCI Card).

I'm using the bcm43xx kernel module with kernel version 2.6.15-23-i386 and not using the ndiswrapper.

iwconfig returns:

```
root@kobold:~# iwconfig
lo        no wireless extensions.

eth0    no wireless extensions.

eth1    IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
        Mode:Managed  Access Point: Invalid   Bit Rate=11 Mb/s
        RTS thr:off   Fragment thr:off
        Encryption key:off
        Link Quality:0  Signal level:0  Noise level:0
        Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
        Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0     no wireless extensions.
```

Now my problem starts when I run [FONT="Courier New"][COLOR="Blue"]iwlist scan[/COLOR][/FONT].
As a user it returns:
```
gabe@kobold:~$ iwlist eth1 scan
[COLOR="Red"]eth1    No scan results[/COLOR]
```

However, when run as root it returns:
```
root@kobold:~# iwlist eth1 scan
[COLOR="Red"]eth1    Interface doesn't support scanning : No such device[/COLOR]
```

Does anybody know what causes the difference in results between root and a  normal user?

---

