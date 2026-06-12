---
title: "Ethernet problem"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by bossa on 2009-01-23
Hi All
Got a strange problem happening with my Foxconn NF4UK8AA-8EKRS Skt 939 ,booted up only to find there was no internet connection. Router said I was connected, but no go . Anyway I had a NIC card so chucked that in and connected no worries.Next day booted up ....no connection :? I thought thats it then, the board has had it :cry: .One last try connected the cable back in the ethernet port (onboard) ...and connected :o
Now its hit and miss which one works. One day the NIC will work the next time the on-board will. Dont know if its a matter of time before it just stops connecting. Also tried disabling on board lan in the bios, but then neither would connect
Anyone heard of this kind of problem ? is this a problem with the board or the OS I have been running Ubuntu for a long time now and had no problem, is there anything I can do or should I look for a new board ? ....skt 939 boards seem to be rare (anyone got one spare let me know (UK)
Any Ideas
Steve

---

### Post by superprash2003 on 2009-01-23
post output of ifconfig from the terminal

---

### Post by bossa on 2009-01-23
Hi superprash2003

heres what it says

steve@kde:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:58:13:62:c1
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x8000

eth1      Link encap:Ethernet  HWaddr 00:e0:4d:08:d4:01
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4dff:fe08:d401/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5744 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4714205 (4.7 MB)  TX bytes:1092082 (1.0 MB)
          Interrupt:19 Base address:0xac00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3400 (3.4 KB)  TX bytes:3400 (3.4 KB)

Right now I'm connected via the NIC eth1

---

### Post by bossa on 2009-01-25
bump ?

---

### Post by superprash2003 on 2009-02-06
is this ifconfig posted when everything was fine?? post output of ping 192.168.1.1   .. presuming your router ip is 192.168.1.1

---

