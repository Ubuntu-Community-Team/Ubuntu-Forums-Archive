---
title: "eth0 fixed IP. How to use eth1 for Internet?"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by fopetesl on 2009-08-07
5.10 Breezy configured as machine controller.  Works great :D
eth0 is a fixed IP to communicate with controller comms board.
Not easy at all to alter - the comms board is hard coded to listen on eth0 for commands.

I would like to use eth1 to link to Internet so I can interrogate the system remotely and it must have DHCP enabled.

Googling hasn't given me an answer yet.

Where to find HOWTO?

---

### Post by Iowan on 2009-08-07
Is Breezy a desktop or server (I just happen to have a Breezy server... still)? Configuration would be via */etc/network/interfaces*. I may need to re-discover some of the details. 
(Out of curiosity, what kind of machine controller?)

---

### Post by superprash2003 on 2009-08-07
you could use ssh for this ..

---

### Post by fopetesl on 2009-08-07
> **Iowan said:**
> Is Breezy a desktop or server (I just happen to have a Breezy server... still)? Configuration would be via */etc/network/interfaces*. I may need to re-discover some of the details. It's a desktop and I looked in *interfaces* but not sure how to edit correctly :(> (Out of curiosity, what kind of machine controller?)Sort of test equipment.  Scanning head moves over sample. Collects results and passes the data to the comms controller thence via LAN to the mainboard.  Would be real nice to collect (& control) it over the Internet.:lol:

---

### Post by fopetesl on 2009-08-07
> **superprash2003 said:**
> you could use ssh for this ..Thanks super but I'd still need to set up eth1. No?

---

### Post by Aximilli on 2009-08-07
I think that this is the same thing I am looking for. I also have a server with two nic cards, one for image pushing and one for everything else. 

eth0 is configed for DHCP and is how I ssh in. eth1 is static for imaging. but whenever I download updates or new packages my network monitor tells me it is downloading through eth1. 

is there a way to either a) specify a card for internet use, or b) restrict eth1 to local traffic, forcing the box to use eth0.

Sorry to piggyback, but I think the answer to both our problems might be the same.

---

### Post by Aximilli on 2009-08-07
> **fopetesl said:**
> 

I would like to use eth1 to link to Internet so I can interrogate the system remotely and it must have DHCP enabled.

you might need something like this in /etc/network/interfaces

```

auto eth1
iface eth1 inet dhcp

```

that could be it for you.

---

### Post by fopetesl on 2009-08-08
OK Aximilli, piggy back is good :D

I'm fairly certain I've been down this route> auto eth1
iface eth1 inet dhcp via the network manager GUI.

The problem, configuring eth1 as per above, as I see it for me is that when I fire up Firefox or try to ping external IPs the 'system' always tries to use eth0.  Maybe I'm missing something :(

I haven't used ssh (yet) but is it possible to force the system to listen on eth1 whilst utilising eth0 for internal processes?

---

### Post by Iowan on 2009-08-08
I don't have a good, solid "Here's how" answer, but I suspect **route** will help.  **man route** should help with details.  Otherwise, it may be an **iptables** thing (something I know even less about...)

---

### Post by fopetesl on 2009-08-08
> **Iowan said:**
> I don't have a good, solid "Here's how" answer, but I suspect **route** will help.  **man route** should help with details.  Otherwise, it may be an **iptables** thing (something I know even less about...)I'll have a look at it tomorrow and come back :)

---

### Post by garikaib on 2009-08-08
Have you tried using the route command. Try this :

route add default eth1

---

### Post by fopetesl on 2009-08-08
> **garikaib said:**
> Have you tried using the route command. Try this :

route add default eth1Thanks garikaib, will test tomorrow and let everyone know :P

---

### Post by fopetesl on 2009-08-09
Well, I've done the *route* and ..*interfaces*.
Now (without eth0 connected to anything) I can ping google so that's switched eth1 ON.
Have I now bypassed eth0 so I can't communicate with the controller? :confused:
I have to set up some gear so I'll check back tomorrow.

---

### Post by fopetesl on 2009-08-17
'Fraid not the answer :(
I can use eth1 as the default gateway and ping google.com, etc.

But when I now attempt to communicate with the controller with netcat, e.g.```
echo !HH | nc 192.168.1.6 80
```I obviously never get an answer since the request is passed via eth1.

Using the -g option with netcat doesn't work either.

Any suggestions as to how I can still use eth0 as my communication port to the controller?

---

