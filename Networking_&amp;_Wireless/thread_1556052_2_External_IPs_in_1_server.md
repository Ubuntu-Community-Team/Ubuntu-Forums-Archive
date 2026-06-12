---
title: "2 External IPs in 1 server"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by LepeKaname on 2010-08-18
Hello, I'm having some problems to setup 2 external (non-local) IPs in a server. This is my /etc/network/interfaces (I modified the real IPs and omitted lo and eth0 as I think is irrelevant):

```
auto eth1
iface eth1 inet static
address 1.1.1.197
netmask 255.255.255.248
#gateway 1.1.1.193
#dns-nameservers 1.1.1.75
#broadcast 1.1.1.199

auto eth2
iface eth2 inet static
address 1.1.1.198
netmask 255.255.255.248
#gateway 1.1.1.193
#dns-nameservers 1.1.1.75
#broadcast 1.1.1.199
```

The output of ifconfig -a is:

```
eth1      Link encap:Ethernet  HWaddr 00:1d:73:78:e1:38  
          inet addr:1.1.1.197  Bcast:1.1.1.199  Mask:255.255.255.248
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:437 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28487 (28.4 KB)  TX bytes:5184 (5.1 KB)
          Interrupt:21 Base address:0xc00 

eth2      Link encap:Ethernet  HWaddr 00:40:26:bb:a4:cd  
          inet addr:1.1.1.198  Bcast:1.1.1.199  Mask:255.255.255.248
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:531 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35178 (35.1 KB)  TX bytes:4612 (4.6 KB)
          Interrupt:23 Base address:0xec00 
```


If I ping to ...198 it respond correctly. However ...197 times out.

So I disabled eth1 and eth2 to perform some testing: 
```
ifconfig eth1 down; ifconfig eth2 down.
```

If I enable eth1 (ifconfig eth1 up), ...198 respond correctly (Please note that eth1 was supposed ...197 and not ...198)
The same happens otherwise, if I enable eth2 (theoretically ...198) but not eth1, ...197 respond correctly...

This is the first time I try a setup like this one. Could someone point me into the right direction please?

Thank you!

---

### Post by LepeKaname on 2010-08-18
I managed to be able to ping to both eth1 and eth2.
I just removed the "auto eth1" and "auto eth2"...
Could someone explain me what exactly that stanza do?
I read the "man interface" and it is still not clear for me:

> Lines beginning with the word "auto" are used to identify the physical interfaces to be brought up when ifup is run with the -a option.   (This  option is  used  by the system boot scripts.)  Physical interface names should follow the word "auto" on the same line.  There can be multiple "auto" stanzas. ifup brings the named interfaces up in the order listed.

So, it is required for a static setting? Does not having that stanza affects other system scripts?

I'm confused... I'm not sure if I should mark this thread as "solved"...

---

### Post by LepeKaname on 2010-08-22
After rebooting the system I was unable to connect to the server... :(
so I guessed that the "auto eth*" was related to it (now I know what "auto" is for). 
I added again those stanzas (as it was in the very beginning) and started those interfaces using "ifconfig". 
Both interfaces worked right away. I rebooted the system to be sure if the setting was working properly and it was.

What I don't understand is why it was not working before... Does rebooting was necessary? Maybe I will never know.

---

