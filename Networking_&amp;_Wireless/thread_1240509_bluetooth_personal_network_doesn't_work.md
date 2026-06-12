---
title: "bluetooth personal network doesn't work"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by Selmi on 2009-08-14
ubuntu is 9.04 (jaunty) with all updates. 

i have pc connected to internet using ethernet (eth1). there is also working connection sharing, so another computer on local network connected to eth0 can connect to internet using my pc. this connection sharing works without problems

now i want to make it possible to connect to my pc using bluetooth and use its internet connection from my notebook and handheld

first i tried some tutorials i found, they all used pand - but this is not available on ubuntu 9.04. i installed bluez-compat, but still, i wasn't able to make it work. so i looked some more and found someone recommending blueman. i installed it from ppa.launchpad.net and i have version 1.10

i restarted machine (just in case) but when i go to local services/network and enable 'network access point (nap)' then on apply it says
```
dnsmasq: failed to bind DHCP server socket: Address already in use
```. same message is shown always when i log in

also when i try to connect from notebook i get error on remote device and on my pc in syslog last line is
```
Aug 15 00:37:52 selmipc bluetoothd[3318]: Hangup or error on BNEP socket
```

any idea what is wrong and how can i solve it?

dnsmasq is working for my shared ethernet connection, i am sure of it. why it doesn't want to work for bluetooth too? i am not network guru, so maybe i am completely wrong, but i believe that one dhcp server is enough to handle all network interfaces when needed..or is there some catch?

if possible i would need some step-by-step tutorial for newbies, maybe such docs would be interesting for some others too.

thanks in advance

---

### Post by walmis on 2009-08-20
You need to configure dnsmasq to bind to the interface you need, as you can see by default it binds to all network interfaces including bluetooth ones, so blueman cannot launch it's own instance of dnsmasq, hence it fails with "address already in use"

---

### Post by Selmi on 2009-08-28
on another pc i tried to make the same, there was no dnsmasq conflict, and everything was working day ago in ubuntu 8.10 32bit

then i reinstalled system to ubuntu 9.04 64bit and since then i can't connect to NAT anymore, error is only in /var/log/syslog, it says bluetoothd[3318]: Hangup or error on BNEP socket

so it seems like some problem in ubuntu 9.04 64bit to me. for now i made bugreport to blueman about this and i will see if it will be solved somehow

[https://bugs.edge.launchpad.net/blueman/+bug/420722](https://bugs.edge.launchpad.net/blueman/+bug/420722)

---

### Post by Selmi on 2009-09-21
just to let everyone who will have similar problems.

Valmantas Palikša told me to try setting DisableSecurity=true in /etc/bluetooth/network.conf

it helped

---

