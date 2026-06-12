---
title: "/etc/network/interfaces gateway definition ignored"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by sgtrock on 2010-07-22
This one is driving me crazy.  Currently running 

```
jim@tesla:/etc/network$ uname -a
Linux tesla 2.6.28-18-generic #60-Ubuntu SMP Fri Mar 12 04:26:47 UTC 2010 x86_64 GNU/Linux
```


I recently changed my default router from 192.168.1.1 to 192.168.1.2 due to some equipment changes.  I can force the change at will with:
```

route add default gw 192.168.1.2
route del default gw 192.168.1.1
```

I've made the change to /etc/network/interfaces to make it permanent:

```
jim@tesla:/etc/network$ cat interfaces
auto lo eth0
iface lo inet loopback

iface eth0 inet static
        address 192.168.1.53
        netmask 255.255.255.0
        gateway 192.168.1.2
```

However, whenever I reboot, the route statement is still showing the old default gateway!  I run the two 'route' commands and everything is good again.

I can't find anything in the logs to tell me where the old gateway definition is coming from.  Can someone tell me where I should start looking?

TIA

---

### Post by Iowan on 2010-07-22
I've seen posts that say NM overwrites/overrules */etc/network/interfaces*, but it would be curious that the IP address works while the gateway doesn't. (I'm not familiar w/ Kubuntu, though...)

---

### Post by dineshs on 2010-07-23
A doubt Because I am learning.
> auto lo [COLOR="Blue"]eth0[/COLOR]
iface lo inet loopback

iface eth0 inet static
        address 192.168.1.53
        netmask 255.255.255.0
        gateway 192.168.1.2
Mine is

```
auto lo
iface lo inet loopback

[COLOR="Blue"]auto eth0[/COLOR]
iface eth0 inet static
    address 192.168.1.53
    netmask 255.255.255.0
    gateway 192.168.1.2
```

Will it be a problem?

---

### Post by Iowan on 2010-07-23
Either way *should* work.

---

### Post by sgtrock on 2010-07-23
> **Iowan said:**
> I've seen posts that say NM overwrites/overrules */etc/network/interfaces*, but it would be curious that the IP address works while the gateway doesn't. (I'm not familiar w/ Kubuntu, though...)

I had heard the same thing about Network Manager.  However, I can't find any documentation about it.  Do you know where the configuration files are for it?

---

### Post by johnlatz on 2010-07-26
Or how to disable NM and revert to the old fashioned CLI sledgehammer approach?

---

### Post by sgtrock on 2010-07-27
As it turns out, this was NOT Network Manager messing with my head.  Instead, it was wicd.  I had forgotten that I installed wicd a long, long time ago.  A quick visit to the GUI for wicd and I was back in business.

This does raise the question, though.  Why did Network Manager and wicd BOTH decide to create their own configuration files instead of just using the default that already existed?

---

