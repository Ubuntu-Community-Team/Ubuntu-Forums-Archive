---
title: "DHCP &quot;pass through&quot; help request."
date: 2011-07-22
forum: Networking &amp; Wireless
---

### Post by DaMonkey on 2011-07-22
Hi all,

I need help with setting up some sort of "dhcp pass through" on an ubuntu internet router.

This is my situation:
I live in belgium, and have "Telenet" as a provider for internet and digital television.
To have full functionality on the digital television, the digital receiver needs an IP adres.
Telenet places 1 cable modem, with 1 ethernet connection, for all the connections (internet and digital tv). Depending on the MAC address of the requesting device (the digital receiver is registered by them), they return a public ip (81.x.x.x) for internet, or a "local" ip (10.x.x.x) for digital tv.
The normal setup is to have:

Cable modem - switch < (1 and 2)
1) router - computers
2) digital tv

The problem with this is, I would need 2 ethernet cables in every room, but this is impossible for me.

Is there a way to setup some sort of dhcp pass through depending on the MAC address?

So that can have:

Cable modem - ubuntu router - gigabit switch < (1 and 2)
1) digital tv
2) computer

and have the computers on the switch get an ip from the ubuntu router, but the digital tv get an ip from the cable modem?

Thanks for your support.

---

### Post by regala on 2011-07-22
> **DaMonkey said:**
> Hi all,

I need help with setting up some sort of "dhcp pass through" on an ubuntu internet router.

This is my situation:
I live in belgium, and have "Telenet" as a provider for internet and digital television.
To have full functionality on the digital television, the digital receiver needs an IP adres.
Telenet places 1 cable modem, with 1 ethernet connection, for all the connections (internet and digital tv). Depending on the MAC address of the requesting device (the digital receiver is registered by them), they return a public ip (81.x.x.x) for internet, or a "local" ip (10.x.x.x) for digital tv.
The normal setup is to have:

Cable modem - switch < (1 and 2)
1) router - computers
2) digital tv

The problem with this is, I would need 2 ethernet cables in every room, but this is impossible for me.

Is there a way to setup some sort of dhcp pass through depending on the MAC address?

So that can have:

Cable modem - ubuntu router - gigabit switch < (1 and 2)
1) digital tv
2) computer

and have the computers on the switch get an ip from the ubuntu router, but the digital tv get an ip from the cable modem?

Thanks for your support.

dhcp relay

---

### Post by DaMonkey on 2011-07-22
Hi regela,

Thanks for your reply.
I was looking into this, but could not really tell if this is what I needed.
I only find info about this being used for balancing between servers...
Do you know a howto/guide for what I need?

All my traffic has to pass through my server.

Thanks again.

---

