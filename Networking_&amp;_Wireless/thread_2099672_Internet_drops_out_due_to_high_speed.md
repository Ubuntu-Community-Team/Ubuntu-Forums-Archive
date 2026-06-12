---
title: "Internet drops out due to high speed ?"
date: 2012-12-30
forum: Networking &amp; Wireless
---

### Post by Harm133 on 2012-12-30
Hey there :),

I've just installed ubuntu via the wubi installer. I've had quite some problems with the 12.10 version and decided to stick with the 12.04 version.

Seems like all is fine so far but there is one problem.
My internet is working fine for doing the normal stuff, email browsing chatting etc.

The problem I have is when I try to speedtest my connection or download stuff from servers with capacity to give me my maximum download speed. I have 120Mbit/s internet but when I speedtest at speedtest.net it goes to 120 but then my network card drops out. after a few secs it starts up again at way lower speed and goes to 120Mbit again and drops out etc etc.

I've tried forcing my network card to use 100mbit and that seems to work a bit better since it now only drops if it gets above 90Mbit. though this is of course a problem.

This is my info I think is relevant :

```
sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:00:00:00:00:00 :)
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-4 ip=10.0.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:65 memory:fb600000-fb61ffff memory:fb628000-fb628fff ioport:f040(size=32)

```

---

### Post by Andy45 on 2012-12-30
How old is your network card? It may not be up to par with today's blazing fast internet speeds ;)

---

### Post by haqking on 2012-12-30
> **Andy45 said:**
> How old is your network card? It may not be up to par with today's blazing fast internet speeds ;)

if you read the OP you would see it is a gigabit card as are most ethernet cards these days.

To the OP, does it work in Windows as i see this is in Wubi ?

If not in Windows then it may be your router/modem as 120 would be vDSL or similar and your router/modem would need to be an upto date one to cope with that connection.

Peace

---

### Post by Harm133 on 2012-12-30
In windows 7 I get the full 120Mbits :)

---

