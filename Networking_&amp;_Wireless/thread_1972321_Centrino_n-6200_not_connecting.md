---
title: "Centrino n-6200 not connecting"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by reh2ur on 2012-05-03
Hi there. 
I'm new with ubuntu, so sry for stupid questions ;)

I use an intel centrino n-6200 wireless card with ubuntu 12 (in 11 i had the same problem).

When i switch on WLAN i can find my fritzbox 6360, but after it asks for the WPA2 key, nothing happens. 
It's just connecting some time and asking me again for the key (which is correct).

If have no clue, where to start searching :D

If anyone could help me step by step? :)

reh2ur

---

### Post by mattisan on 2012-05-28
> **reh2ur said:**
> Hi there. 
I'm new with ubuntu, so sry for stupid questions ;)

I use an intel centrino n-6200 wireless card with ubuntu 12 (in 11 i had the same problem).

When i switch on WLAN i can find my fritzbox 6360, but after it asks for the WPA2 key, nothing happens. 
It's just connecting some time and asking me again for the key (which is correct).

If have no clue, where to start searching :D

If anyone could help me step by step? :)

reh2ur

Exactly the same problem with the Centrino N-6200 attempting to connect to a DD-WRT driven Linksys E3000. Other wireless cards seem to work just fine (2x DLink N Nano).

---

### Post by linuxman94 on 2012-05-28
Can you post the output of these commands in code tags (# sign)?

```

sudo iwlist wlan0 scan 
dmesg | grep -e wlan -e iwlagn 
```

---

