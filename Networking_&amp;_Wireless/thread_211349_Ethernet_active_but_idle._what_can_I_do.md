---
title: "Ethernet active but idle. what can I do?"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by mco on 2006-07-08
I have to conections, a wireless one and a cable one. Both of them worked the first minutes after I installed ubuntu. Now none of them work (I dont know why because nothing has changed)

Windows works perfectly with the same configuration so it is not an issue of configuration.

I'm attaching some screen shoots that may explain my problem, as you will see everything seems to be ok but the status is idle.

Thank you so much in advance

IFCONFIG: (by the way I dont know what the Bcast is, it resembles  to the Gateway, but my gateway is 192.168.1.25 )

qwerty@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:08:02:2D:AC:5A
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe2d:ac5a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1834 (1.7 KiB)  TX bytes:738 (738.0 b)
          Interrupt:11 Base address:0x1400

eth1      Link encap:Ethernet  HWaddr 00:50:8B:D0:E5:C9
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8bff:fed0:e5c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:48328 (47.1 KiB)  TX bytes:648 (648.0 b)
          Interrupt:3 Base address:0x100

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1012932 (989.1 KiB)  TX bytes:1012932 (989.1 KiB)

[IMG]file:///D:/pro/123.png[/IMG][IMG]file:///D:/pro/1234.png[/IMG][IMG][IMG][IMG]file:///D:/pro/Screenshot-Network%20settings.png[/IMG][/IMG][/IMG]

---

### Post by mco on 2006-07-08
Sorry, the pics...

---

### Post by bforbes on 2006-07-08
What happens when you ping the gateway?

---

### Post by mco on 2006-07-08
"Host unreachable" of course. I think the problem has to do with the network card, a realtek 8139. As I've been reading it seems  many people started having problems with it since updating to Drapper... My ubuntu is the 5.04 version

---

### Post by bforbes on 2006-07-08
Try:
```

sudo ifdown eth0
sudo ifup eth0
sudo ifdown eth1
sudo ifup eth1
ping 192.168.1.25

```

---

### Post by mco on 2006-07-08
host unreachable again...

---

### Post by mco on 2006-07-08
Well is not that it is not working u know, I mean 452.3kb have been received and 97.6 have been sent since the last time I logged in.

In fact sometimes another kb is sent or received... its kind of weird... the status is mainly idle but sometimes works again for a second

It must be linked with the realtek, im almost convinced

---

### Post by mips on 2006-07-08
Your answer is here, [http://www.ubuntuforums.org/showthread.php?t=117356](http://www.ubuntuforums.org/showthread.php?t=117356)  and somewhere else that I cannot find right now.

If you are going to say, "But windows...", windows breaks the rules.

---

