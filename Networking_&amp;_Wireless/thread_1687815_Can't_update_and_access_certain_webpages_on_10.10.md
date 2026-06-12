---
title: "Can't update and access certain webpages on 10.10"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by The_Eggert on 2011-02-14
Hello all :)
My father finally let me install Ubuntu on his desktop.
*Great, I can finally show him how great Ubuntu is :D *

But no...When the installation had finished I had no Internet access on the computer.
Or..it's not exactly **NO** Internet access - I am able to enter Google (at least that's the only one I've managed to enter - And yes, I've tried more than one..). Furthermore, I am not able to update the system..

This presentation of Ubuntu didn't exactly go as planned, but I am beginning to feel a bit stubborn, and this *has* to get working, so if anyone is able to help I would greatly appreciate it :)

For starters:
The computer is running Ubuntu 10.10 64-bit
I've attached the output of 'ifconfig -a'
Other than that, I don't know what information will be relevant, so please ask for whatever is needed to (hopefully) get this to work :P

---

### Post by An Sanct on 2011-02-14
Are the settings all okay?
Are you on a DHCP-ed network or did you set Address, Gateway, Netmask, DNS server manually?

PS. that 0x[COLOR=Red]dead[/COLOR] looks bad to me too .... seems like an IRQ failiure of some kind ....[COLOR=Red]
[/COLOR]

---

### Post by The_Eggert on 2011-02-14
> **An Sanct said:**
> Are the settings all okay?
Are you on a DHCP-ed network or did you set Address, Gateway, Netmask, DNS server manually?

I tried setting them "by hand", but that didn't do anything..
But yes, it is currently on a DHCP network :)

---

### Post by An Sanct on 2011-02-14
Okay, if the router is configured OK, then its best to keep it DHCP ;)

Take a look at [this forum thread]("http://ubuntuforums.org/archive/index.php/t-1042940.html") in short, it tells you to shutdown, power-up the network and try again...

Keep us informed ;)

PS. If you need a simple and easy to remember DNS address, 8.8.8.8 is google DNS.

PS2.... also take a look here, for [maverick]("http://gs1.ubuntuforums.org/showthread.php?t=1615318")

---

### Post by An Sanct on 2011-02-14
Try these commands
```
sudo su
ifconfig -a
ifconfig eth0 down
ifconfig eth0 up
dhclient                                 

```

---

### Post by The_Eggert on 2011-02-14
> **An Sanct said:**
> Try these commands
```
sudo su
ifconfig -a
ifconfig eth0 down
ifconfig eth0 up
dhclient                                 

```

I tried that, and it didn't seem to have any effect :P

I'm going to try out those suggestions in the other threads for now - But the funny thing is, the speed of the network isn't slow as such, but I can only access a few selected sites (which open as fast as I would expect) - Others just "stand still", and eventually time out.. (Don't know if that made sense to anyone other than me :P )

But I'll get back with some results once I have any.. ;)

---

### Post by The_Eggert on 2011-02-14
> **An Sanct said:**
> Okay, if the router is configured OK, then its best to keep it DHCP ;)

Take a look at [this forum thread]("http://ubuntuforums.org/archive/index.php/t-1042940.html") in short, it tells you to shutdown, power-up the network and try again...

Keep us informed ;)

PS. If you need a simple and easy to remember DNS address, 8.8.8.8 is google DNS.

PS2.... also take a look here, for [maverick]("http://gs1.ubuntuforums.org/showthread.php?t=1615318")

First of - I forgot, I always set my DNS to Googles ;)

But that's not really the point..I read around in the threads you supplied and apparently it turned out, that changing the MTU value did the job - I am now able to fully browse the internet and update the computer :)

So thanks a billion :D - Now I just got to prove to my dad that the trouble was worth it :D

---

