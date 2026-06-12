---
title: "Intel 5100 not working in ubuntu 12.04"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by CatJackson on 2013-02-04
Hello,

I have installed ubuntu 12.04 in my laptop.
It has an Intel 5100 wifi link and the wireless is not working!

I have googled and tried the:
- edit the /etc/modprobe.d/disable.conf trick
- replaced the firmware for the driver

Is there any idea of what to do next? Is this problem fixed in a newer version of the kernel? If so, which one?
Could you please advise?

This bug is UNTHINKABLE and UNACCEPTABLE in a LTS version of Ubuntu.... :(

Cheers,
Cat

---

### Post by ahallubuntu on 2013-02-04
~

---

### Post by CatJackson on 2013-02-05
Hello ahallubuntu,
Thanks for your reply.

I own a Toshiba TECRA from 2008/2009... Can't be sure on the date.
The specs are:

Intel Core 2 Duo P8600 2.4 GHz, with 2.9 GB RAM.
As for the internet interfaces:
```
ricc@lp-ricc:~$ lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
02:00.0 Network controller: Intel Corporation WiFi Link 5100

```

Regarding your suggested commands, here's the output I get from them:
```
ricc@lp-ricc:~$ /usr/sbin/rfkill list all
0: Toshiba Bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

The wifi/bluetooth card is activated with a manual switch, so there's no key combination that can save me :(
And yes, it's on the proper position ;)

Some extra info:
```
ricc@lp-ricc:~$ uname -a
Linux lp-ricc 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
ricc@lp-ricc:~$ /sbin/ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:7e:ff:cb:ba  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:ffcc0000-ffce0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1353 (1.3 KB)  TX bytes:1353 (1.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:21:6b:d1:3e:7e  
          inet addr:172.17.135.138  Bcast:172.17.135.255  Mask:255.255.252.0
          inet6 addr: fe80::221:6bff:fed1:3e7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:647 (647.0 B)  TX bytes:30022 (30.0 KB)

```


Many thanks for your help!
Cheers,
Cat

---

