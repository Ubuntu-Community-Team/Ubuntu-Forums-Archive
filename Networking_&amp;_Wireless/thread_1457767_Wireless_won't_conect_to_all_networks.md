---
title: "Wireless won't conect to all networks"
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by egrimisu on 2010-04-19
Hi,
I just installed ubuntu 9.10 everithing works smooth but the wireless won't discover all the networks. At home per example won't detect my WPA2 wireless router and my other router that has no security enabled. At work the wpa2 router and the wpa ones are discovered and working charmly. At my parents home the router is not recognizez(no security).

The lan card is an Intel Wifi 4965AGN.

What to do next?

---

### Post by dE_logics on 2010-04-19
You are most probably using wireless-tools to manager and connect to your network, that does not support WPA but wpa_supplicant does.

---

### Post by egrimisu on 2010-10-13
> **dE_logics said:**
> You are most probably using wireless-tools to manager and connect to your network, that does not support WPA but wpa_supplicant does.

and what to use instead?

---

### Post by Peter09 on 2010-10-13
Can you post the output of
 
```
ifconfig
```
 
and
 
```
lshw -C network
```
 
Note: do this with your wired connection disconnected.

---

