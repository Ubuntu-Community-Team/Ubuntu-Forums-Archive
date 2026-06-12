---
title: "'ifconfig' not showing correct IP !!"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by chinmaya_n on 2009-08-12
hi

I observed that ifconfig command doesnt show up correct IP address of mine,
Eventhough i'm connected to internet, There is no sign of connectivity in 'Network Connections' !! 
Can anyone plz.. help me!

Thanx.

---

### Post by host47 on 2009-08-12
Paste the output of ifconfig.

Are you using ethernet o wifi?

---

### Post by Iowan on 2009-08-12
What leads you to the conclusion that **ifconfig** shows the wrong IP? It may be showing the local IP versus the router's/modem's outside IP address (assuming router or modem to connect to Internet).
As far as the connectivity indicator, it's possible to set up addressing through */etc/network/interfaces* that works, but Network Manager (probably responsible for "Network Connections") knows nothing about.

---

### Post by chinmaya_n on 2009-08-13
I'm using a wired connection
```

chinmaya@chinmaya-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:78:bb:32  
          inet addr:172.18.0.12  Bcast:172.18.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:fe78:bb32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:5000  Metric:1
          RX packets:235519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:266576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:133248955 (133.2 MB)  TX bytes:117185673 (117.1 MB)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8368 (8.3 KB)  TX bytes:8368 (8.3 KB) 

```

I saw my ip address in [http://whatismyipaddress.com/](http://whatismyipaddress.com/)
So i thought that ifconfig might not be showing correct address...

But when i tried "http://172.18.0.12/" (ip shown by ifconfig) browser shows "IT WORKS" So it might be local address.
When i tried my real ip (let 000.000.000.000) "http://000.000.000.000" it shows an error saying "could not connect to remote server.

---

### Post by host47 on 2009-08-13
Yes, ifconfig shows you your *local* IP address. Your public address (from the internet router/modem) is what is shown in that kind of web sites you say.

If you try to connect to your own computer, you have to use your local address.

There is no such concept of real IP, only exist public and private (local) address.

---

### Post by chinmaya_n on 2009-08-15
Oops............ 
I dont know anything ab't that!

I'm now working on drupal, now I would like to show my site to others (my friends) by "http://myip/sitename"

How could i show that now?!! 
Can anyone plz help me!:(

---

### Post by dmizer on 2009-08-15
> **chinmaya_n said:**
> Oops............ 
I dont know anything ab't that!

I'm now working on drupal, now I would like to show my site to others (my friends) by "http://myip/sitename"

How could i show that now?!! 
Can anyone plz help me!:(

That's probably worth a new thread.

---

### Post by chinmaya_n on 2009-08-17
Ok, I'm starting a new thread for this problem. It is here :
[http://ubuntuforums.org/showthread.php?p=7800521#post7800521](http://ubuntuforums.org/showthread.php?p=7800521#post7800521)

Thanx.

---

