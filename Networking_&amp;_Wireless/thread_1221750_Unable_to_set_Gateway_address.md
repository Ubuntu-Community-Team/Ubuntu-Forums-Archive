---
title: "Unable to set Gateway address"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by envegnomed on 2009-07-24
I am evaluating Ubuntu 9.04 in a corporate network and IP addresses are static, there is no DHCP server for the section I work in. Using the Ubuntu 9.04 live cd I am unable to get my manual IP connection working properly. The problem lies with setting my gateway address. The network applet keeps resetting the gateway address to 0.0.0.0. How can I resolve this issue?

---

### Post by jamest09 on 2009-07-24
> **envegnomed said:**
> I am evaluating Ubuntu 9.04 in a corporate network and IP addresses are static, there is no DHCP server for the section I work in. Using the Ubuntu 9.04 live cd I am unable to get my manual IP connection working properly. The problem lies with setting my gateway address. The network applet keeps resetting the gateway address to 0.0.0.0. How can I resolve this issue?

```
route add default gw 10.1.1.1 eth0
```

Change IP and interface to suit

---

### Post by roadworrier on 2013-03-07
I have the same problem. 10.04. I set the gateway in the GUI, but it doesn't keep, and doesn't work. If I open the GUI again, all the other settings are saved, but the gateway goes back to 0.0.0.0. If I set via 'route add default gw 10.1.1.1 eth0' it works while the server is up, but on reboot the gateway is lost and set back to 0.0.0.0

---

### Post by roadworrier on 2013-03-07
There was no eth1 section in  /etc/network/interfaces even though the IP was stored properly after a reboot. In any case I added this after the loopback address:

auto eth1
iface eth1 inet static
address 172.16.11.40
netmask 255.255.255.0
gateway 172.16.11.1

(Obviously in my reply above I was actually doing 'route add default gw 172.16.11.1 eth1'  for my own purposes... but that did not persist.)

---

