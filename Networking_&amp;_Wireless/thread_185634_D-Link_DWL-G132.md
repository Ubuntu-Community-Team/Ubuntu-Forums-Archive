---
title: "D-Link DWL-G132"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by AustinMini on 2006-06-01
Alright, heres my problem, i have gone through all of the steps of ndiswrapper, and everything worked fine.

```
austin@Austin:~$ ndiswrapper -l
Installed ndis drivers:
athfmwdl        driver present, hardware present
neta5agu        driver present, hardware present

```

```
austin@Austin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:6E:E0:CA:01
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fee0:ca01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3525318 (3.3 MiB)  TX bytes:361443 (352.9 KiB)
          Base address:0xcf80 Memory:fe9e0000-fea00000

lo        Link encap:Local Loopback
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:104653 (102.2 KiB)  TX bytes:104653 (102.2 KiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::192.168.0.104/96 Scope:Compat
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```
austin@Austin:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```


The drivers were installed fine and the hardware is detected. But no wireless connection shows up in Connection Settings. Ives searched and didnt find one answer. Anybody who has gotten this adapter to work. PLEASE share!.

Thank you in advance.

Austin Warren

---

