---
title: "Easy Bridging in 9.04?"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by Fir3chi3f on 2009-09-17
I live in a dorm room and they only allow one ethernet port per student. I have a laptop and a desktop with two ethernet ports. So, if you haven't figured it out, I would like to connect the desktop to the schools network and my laptop to the desktop.

I have tried just about all of the setting combinations possible in the NetworkManager Applet (local link, shared to other computers, etc.) 

The other thing that I have been trying is editing 

```
/etc/network/interfaces
```

with either:

```
auto bridge01
iface bridge01 inet dhcp
  pre-up ifconfig eth0 down
  pre-up ifconfig eth2 down
  pre-up brctl addbr bridge01
  pre-up brctl addif bridge01 eth0
  pre-up brctl addif bridge01 eth2
  pre-up ifconfig eth0 0.0.0.0
  pre-up ifconfig eth2 0.0.0.0
  post-down ifconfig eth0 down
  post-down ifconfig eth2 down
  post-down ifconfig bridge01 down
  post-down brctl delif bridge01 eth0
  post-down brctl delif bridge01 eth2
  post-down brctl delbr bridge01
```

or just:

```
iface br0 inet dhcp
bridge_ports eth0 eth1
```

Is there something Im missing? is there a simple way?

---

