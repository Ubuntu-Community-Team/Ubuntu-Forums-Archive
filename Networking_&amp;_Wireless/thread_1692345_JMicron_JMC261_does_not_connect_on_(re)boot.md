---
title: "JMicron JMC261 does not connect on (re)boot"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by Nocturna on 2011-02-21
Hi there,

This is a problem I've been searching quite some time for but haven't found a solution for yet (been searching since 9.04...now trying again under 10.10 windows just isn't my cup of tea):

On every (re)boot my shuttle X50v2 doesn't get an ip-address and network manager claims the network cable is not attached (which it is, obviously). Even manually trying to get a lease via the terminal and dhclient just results in a long wait with nothing happening.

However, if I disconnect the cable and plug it back in the connection is up in a matter of seconds. After that dhclient immediately get's a new ip-address.

Via ifconfig I do get all the information, minus a ip4 address. There's no difference between the output of ifconfig before and after the cable replug.

I've tried this under ubuntu, netbook remix and xbmclive but the problem persists. Even different cables / different routers doesn't help.

Anyone any idea what's wrong here? I've read about problems between network manager and dhclient v3 but none of the problems described are the same as I have.

Regards,

Rob.

---

### Post by Nocturna on 2011-02-22
Sorry to reply to my own post but I think I've found the error. The driver used is for JMC260 and it needs to use JMC261. Could anyobdy tell me how to force Ubuntu to use the correct version? I've tried compiling the latest driver sources and loading them with modprobe but to no avail..

---

