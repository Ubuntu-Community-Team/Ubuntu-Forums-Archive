---
title: "Added some loopback ip's and strange behaviour ensues!"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by fizgig on 2010-02-07
I added the following lines to my /etc/rc.local file:

```
ifconfig lo:0 10.10.10.1 netmask 255.255.255.0
ifconfig lo:1 10.10.10.2 netmask 255.255.255.0
ifconfig lo:2 10.10.10.3 netmask 255.255.255.0
ifconfig lo:3 10.10.10.4 netmask 255.255.255.0
```

I can bind to those addresses and communicate just fine between them with some ruby code I'm working on.

I did notice, for some reason, that if I drop to a shell, I can ping any address on that subnet successfully (not just .1 through .4) but, say, 10.10.10.99.  I swear those ip's don't exist anywhere.  My home network is 192.1868.2.x and there is no 10.10.10.x ip's anywhere else but on this one ubuntu machine.

Any idea who's responding to those ping requests?  I'm mystified!

---

### Post by Iowan on 2010-02-07
My guess (stress _guess_) would be that loopback is looping... I can ping random address on 127.0.0.X where my loopback is defined.

---

### Post by capscrew on 2010-02-07
> **fizgig said:**
> I added the following lines to my /etc/rc.local file:

```
ifconfig lo:0 10.10.10.1 netmask 255.255.255.0
ifconfig lo:1 10.10.10.2 netmask 255.255.255.0
ifconfig lo:2 10.10.10.3 netmask 255.255.255.0
ifconfig lo:3 10.10.10.4 netmask 255.255.255.0
```

I can bind to those addresses and communicate just fine between them with some ruby code I'm working on.

I did notice, for some reason, that if I drop to a shell, I can ping any address on that subnet successfully (not just .1 through .4) but, say, 10.10.10.99.  I swear those ip's don't exist anywhere.  My home network is 192.1868.2.x and there is no 10.10.10.x ip's anywhere else but on this one ubuntu machine.

Any idea who's responding to those ping requests?  I'm mystified!

Building on @Iowan's thought, the Wikipedia section on Virtual Interfaces is pertinent.  See [**_[COLOR="Navy"]here[/COLOR]_**]("http://en.wikipedia.org/wiki/Loopback").

As a software based interface replicating a piece of hardware (e.g. the NIC), there is no reason why you can't assign an IP address of your own choice.  This would have all of the features of the default 127.0.0.0/8 network.

In short when you assign the 10.10.10.1 IP address you are actually assigning the entire 10.0.0.0/8 network to the interface *lo0 *interface.

---

### Post by fizgig on 2010-02-08
Fascinating!  Thanks for the information.

---

### Post by capscrew on 2010-02-08
> **fizgig said:**
> ...I can bind to those addresses and communicate just fine between them with some ruby code I'm working on.


Why do you feel you need to change from the 127.0.0.0/8 block of addresses? They are as legitimate as the 10.0.0.0/8 block and were reserved for just the type of work you are doing.

---

### Post by fizgig on 2010-02-08
Fair point.  I might do just that.

---

