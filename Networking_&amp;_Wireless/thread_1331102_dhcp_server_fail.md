---
title: "dhcp server fail"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by Fir3chi3f on 2009-11-19
Little background: In my dorm there is only one ethernet connection and I have a desktop and a laptop. I have been running them off of a switch. I am trying to set up a firewall and connect the laptop threw the desktop (that has two ethernet ports). 

Experimenting with the 'Shared to other computers", static and dhcp have yielded no results. I have installed firestarter and on startup it gives error:
```
The device eth1 is not ready.
```

I also tried to create my own dhcp server but also fails:

```
:~$ sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   
 * check syslog for diagnostics.
 [fail]

```

Although I maybe setting it wrong, I have also experimented with static settings. I don't have anything to put in dns and gateway so I left them blank.

Is there anything else I could try? I have been experimenting with this since 9.04 and 9.10 is the same.

---

### Post by lvlint67 on 2009-11-19
This is a common solution on our campus because they will disable the jack if you plug in a switch (have a ton of those laying around).

our solution usually involved a fresh install of ubuntu-desktop and then firestarter. the wizzard made it easy.

You could try removing any reference in /etc/network/interfaces to anything that isn't the loopback adapter.

---

### Post by Fir3chi3f on 2009-11-19
The isn't loopback 127.0.0.1? what is the loopback adapter? 

I have tried eth0 and eth1 both have the same results (I with each change I only use ctrl+alt+backspace instead of reboot). 

eth0 is connected to the schools network and eth1 to my laptop

---

### Post by Iowan on 2009-11-19
> **Fir3chi3f said:**
> The isn't loopback 127.0.0.1? what is the loopback adapter? 
Ordinarily, */etc/network/interfaces* contains only ```
# The loopback network interface
auto lo
iface lo inet loopback

```Yes, loopback is 127.0.0.1.
The loopback adapter (AKA loopback device) is described [here]("http://en.wikipedia.org/wiki/Loopback").

---

