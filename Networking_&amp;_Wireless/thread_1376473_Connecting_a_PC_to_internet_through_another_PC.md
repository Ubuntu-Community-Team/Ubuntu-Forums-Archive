---
title: "Connecting a PC to internet through another PC"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Arwen17evenstar on 2010-01-09
I have a [COLOR=SeaGreen]desktop[/COLOR] with a wireless usb adapter and a wireless laptop.
The [COLOR=SeaGreen]desktop[/COLOR] has [COLOR=SeaGreen]vista[/COLOR] 64bit and the laptop has ubuntu.

I have another [COLOR=DarkOrange]desktop[/COLOR] I want to wire to either the vista desktop or the laptop. I have an ethernet cable to do this.

I'm going to be installing [COLOR=DarkOrange]ubuntu[/COLOR] on the [COLOR=DarkOrange]desktop[/COLOR]. Is there any way to get it connected to the internet through the [COLOR=SeaGreen]vista desktop[/COLOR] or the ubuntu laptop? Both of these guys are wirelessly connected to the router downstairs. 

Normally, I would just buy a usb wireless adapter, but this is ubuntu. they don't make drivers for that and I don't want to mess around trying to find someone who will.

Also, if I installed [COLOR=Black]ubuntu server[/COLOR] on the [COLOR=DarkOrange]desktop[/COLOR] instead. Would I still be able to connect through the [COLOR=SeaGreen]vista desktop[/COLOR] or ubuntu laptop to get to the internet?

I know the easiest way, in the server's case, would be to plug it into the router downstairs. But I'm curious if that's the only way to get a server connected to the internet.

I know about wireless bridges etc. but that would require me to buy at least 1 more router since I only own one. I'm just trying to figure out what I can do with what I already have.

---

### Post by scragar on 2010-01-09
[https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

It's kind of hacky, but it should work.

---

### Post by Arwen17evenstar on 2010-01-09
> **scragar said:**
> [https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

It's kind of hacky, but it should work.


sooo if I do that and hook up the computers together with the ethernet cable, it'll work?
There's nothing more to it?

---

### Post by scragar on 2010-01-09
It should do, it's not too different from my setup where I have my desktop bridging the connection to my router(the router doesn't have enough connections for all my machines :p).

---

### Post by Iowan on 2010-01-09
> **Arwen17evenstar said:**
> sooo if I do that and hook up the computers together with the ethernet cable, it'll work?
There's nothing more to it?A direct connection between two computers will *probably* require a crossover cable unless you go throuth a switch/hub/router. There are (reportedly) some gigabit adapters that can autoconfigure.
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is another help page that might be useful.

---

