---
title: "Wireless Network Card Disabling at Startup"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by Graxer on 2010-05-14
Since I installed Ubuntu, when starting up my laptop if I choose to start Ubuntu then my wireless card completely deactivates and cannot be used that session. If however I choose Windows my wireless card remains active and works fully.

I have found a, somewhat annoying, solution to this. If manually turn my Wi-Fi card off via the switch on the side of my laptop and don't switch it on until logged into Ubuntu then Wi-Fi works perfectly. It is only the startup process which disables it.

Is there a solution to this, as it gets annoying when I'm using wireless and forget to deactivate my card.

```
description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:56:2c:84
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:f6000000-f6001fff
```I am using Wubi if that is important.

---

### Post by Iowan on 2010-05-14
Is the "Available to all users" box checked on Network Manager's page for wireless?

---

### Post by Graxer on 2010-05-14
> **Iowan said:**
> Is the "Available to all users" box checked on Network Manager's page for wireless?
If you mean the "Network Connections" window's wireless tab I can't see a checkbox there. There is only a list of the wireless connections I have connected to in the past with "Add" "Edit" and "Delete". Also, I am the only user on my laptop, and the card switches off before the log-in screen appears. (My the wireless light on my laptop isn't lit up)

I should probably add that if I turn the switch off and on again once my wireless is disabled the light flashes on for a second then turns off again.

---

### Post by cisforcojo on 2010-05-14
I can confirm this problem.

I'm using a Dell Studio XPS 17 and also have the Intel 5300 AGN card. It was working for a brief bit but a recent update killed it again. I believe it's a problem with network-manager and am looking into it.

---

### Post by Graxer on 2010-05-14
> **cisforcojo said:**
> I can confirm this problem.

I'm using a Dell Studio XPS 17 and also have the Intel 5300 AGN card. It was working for a brief bit but a recent update killed it again. I believe it's a problem with network-manager and am looking into it.
Thanks for the confirmation. In a way it's good to know that I am not the only one with this problem!

I am using a Dell Vostro 1520.

---

### Post by Iowan on 2010-05-14
Although my desktop has no wireless card, if I try to establish a new wireless connection in Network Manager (via right-click>Edit connections), near the Cancel and Apply buttons is an "Available to all users" checkbox (grayed on my machine).

---

### Post by Graxer on 2010-05-14
> **Iowan said:**
> Although my desktop has no wireless card, if I try to establish a new wireless connection in Network Manager (via right-click>Edit connections), near the Cancel and Apply buttons is an "Available to all users" checkbox (grayed on my machine).
Ah, yes, mine has that if I try to edit an existing connection. 

However I don't believe that's the problem as its not a problem with connecting to the networks it can see. It's a problem with the wireless card being activated to detect them in the first place.

---

