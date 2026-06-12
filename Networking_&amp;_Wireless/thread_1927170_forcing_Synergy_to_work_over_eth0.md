---
title: "forcing Synergy to work over eth0?"
date: 2012-02-17
forum: Networking &amp; Wireless
---

### Post by kooldino on 2012-02-17
I have two PCs in front of me.  The one on the left runs Kubuntu 11.10, the one on the right runs Windows 7.  They are both on my local 192.x.x.x network.

On my kubuntu machine, I run the juniper VPN client to connect to my work VPN.  Once I'm connected, I have a tun0 interface, with a 10.x.x.x IP address.  

Once I'm on the VPN, I can no longer remote control my Windows 7 machine (the one that's physically in front of me, on the right) since I'm no longer on the same network, despite eth0 still being on the 192 network.

I tried starting my synergy server with the followng in order to force it to use the network eth0 is on, but I've had no luck:

```
synergys -a 192.168.0.101 -c synergy.conf 
```

Is there a way to use synergy to remote control my Windows 7 machine while still staying on my VPN?

---

### Post by CivilizationII on 2012-02-17
Try:

route add 192.168.0.101 eth0

---

