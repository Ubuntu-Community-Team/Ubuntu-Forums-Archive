---
title: "wired network connection problem with router"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by krivan on 2009-08-20
Hi,

my laptop is behind a [netgear] router and I connect to this through wire. The connection works just under windows unfortunately. I use Ubuntu 9.04.

So the problem is that I cannot get the wired connection properly working however

1. I get IP [DHCP]: ifconfig says 192.168.1.3
2. resolv.conf:   nameserver 192.168.1.1 [the router]
3. /etc/network/interfaces: 
     
     ...
     auto eth0
     iface eth0 inet dhcp


4. ping works
   I can ping the router and other domains as well like ubuntu.com, etc.


But still I can't make it work somehow. If I open the network manager from the menus it is completely empty.

Strange, I can't reach the router settings from firefox either. I contact the router at 192.168.1.1, then user/pass and after login the frames of the page are visible but the pages themselves cannot be loaded.

I tried /etc/init.d/networking restart   as well but no change.

I am clueless at the moment. Has anybody idea what to do? Certainly there is a very straightforward solution for my problem but I can't see it...

Thx,
Krivan

---

### Post by Iowan on 2009-08-21
Mostly as a [bump] for your thread... If you can ping other sites - like ubuntu.com - then the gateway and DNS must be working properly. Network Manager probably ignores your connection - since it was set up in */etc/network/interfaces*.

---

### Post by krivan on 2009-08-22
Hi Iowan,

thanks for the answer!

But I still don't understand. Why would the Network Manager ignore a connection which already had been set up by the /etc/network/interfaces?

I mean that there is IP/DNS/ping works...what should be done to show the Ubuntu [or probably just to the Network Manager] that it is a working internet link? I have tried to set up a cable connection and a DSL connection [I have cable conn.] but no results...

Krivan

---

### Post by krivan on 2009-08-23
EDIT

if I do /etc/init.d/networking restart I get the error message

wmaster0: unknown hardware address type 801

what does this mean?





> **krivan said:**
> Hi Iowan,

thanks for the answer!

But I still don't understand. Why would the Network Manager ignore a connection which already had been set up by the /etc/network/interfaces?

I mean that there is IP/DNS/ping works...what should be done to show the Ubuntu [or probably just to the Network Manager] that it is a working internet link? I have tried to set up a cable connection and a DSL connection [I have cable conn.] but no results...

Krivan

---

### Post by Iowan on 2009-08-23
> **krivan said:**
>  Why would the Network Manager ignore a connection which already had been set up by the /etc/network/interfaces?Because Network Manager seems to handle only one interface at a time, having it ignore interfaces configured in */etc/network/interfaces* makes it possible to have more than one interface active at a time (like "lo", for instance). A few threads have solved their problem by changing ["managed=false"]("http://ubuntuforums.org/showthread.php?t=1028541")

---

