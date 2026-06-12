---
title: "Broadcom 4311 Wireless Issue on Clean install"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by SoulSmasher on 2011-04-06
Hi,

Today, I installed Natty beta 1 and having a Wireless issue, I hope you can help me. I want to use wifi network on my Acer Aspire 5104, but I can't see wireless.

I installed b43-fwcutter and firmware-b43-installer, here are some results.

```
arda@arda-Aspire-5100:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d4:db:61:6d  
          inet addr:192.168.1.37  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fedb:616d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8223652 (8.2 MB)  TX bytes:490216 (490.2 KB)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)
```

```
arda@arda-Aspire-5100:~$ lspci | grep Broadcom
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

How can I enable wireless, what I'm missing ? Back in 10.10 Right after I installed b43-fwcutter , it was configuring itself.
Thanks

---

### Post by erikdstock on 2011-04-07
i am also having this issue on a clean install (hp dv6113us, broadcom bcm4311. 

A wireless switch on the front of the housing does not change from orange (off) to blue as it should and there is no wireless. :(:(

---

### Post by beew on 2011-04-07
I also have wireless problem with broadcom but it seems even more weird. 
[http://ubuntuforums.org/showthread.php?t=1723376](http://ubuntuforums.org/showthread.php?t=1723376)

Current status "activated but not in use"

---

### Post by manzdagratiano on 2011-04-07
Broadcom 4311 is supported by the closed source driver wl, and I do not know how well b43-fwcutter works with it - I have Broadcom 4312, and fwcutter absolutely did not work with it. Uninstall it as well as firmware-b43-installer, and then install bcmwl-kernel-source. You may do these directly by following the guide in:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
if you do not have internet access at the moment.
Note also that the free and proprietary drivers may NOT be simultaneously installed. They conflict each other. If wireless does not work, blacklist b43, b44, b43-legacy, ssb, and brcm80211 in /etc/modules.d/blacklist.conf.
It should work! Mine is working perfectly well with Natty.

---

