---
title: "Netgear WG602 access point problem"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by davemar on 2009-10-29
I've just bought a Netgear WG602 wireless access point, and I'm trying to get it working. The manual states that it be found on IP address 192.168.0.227 (i.e when connected via it's ethernet port). I've tried pinging this address but get no reply. I've tried doing a reset by holding the little button on the back down for ages, but this doesn't seem to do anything. I've even changed my PC's IP address to start 192.168.0 to ensure it's in the same netmask but still no joy.

The power and ethernet lights are green, and the wireless light is flashing amber. Have I got a faulty unit?

---

### Post by tranquito on 2010-04-07
Bump!

---

### Post by Charly85551 on 2010-04-08
Hi Davemar,
don't panic! It is a simple network protocol issue to get access to your WG602. Ensure that your PC's network card is set to something static like: 192.168.0.5 with subnet to 255.255.255.0. When entering [http://192.168.0.227/](http://192.168.0.227/) into your browser you should see the start screen of the WG602 setup screen. If it doesn't come up, try to put a switch in between, since some network cards don't support auto RX/TX-function. Just hope you have a V2 of the WG602 since only V2 will give you WPA2 security.
Good luck
charly85551

---

