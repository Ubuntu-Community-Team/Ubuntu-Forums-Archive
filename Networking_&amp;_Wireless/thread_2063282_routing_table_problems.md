---
title: "routing table problems"
date: 2012-09-26
forum: Networking &amp; Wireless
---

### Post by Anders J on 2012-09-26
Hi there,

I had The Perfect test setup running, using a laptop with the Ethernet connection to a test board using a manually set ip adrdress, while at the same time the WiFi connection was using DHCP for internet, Dropbox.

After i reinstall I could not go back to this ideal situation, because the default ip is directed to the wired connection.

Here's the route table with wifi only:
```
anders@anders-HP-635-Notebook-PC ~/Desktop $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0

```

And here is the same with wired connectio also:
```
anders@anders-HP-635-Notebook-PC ~/Desktop $ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         172.16.0.1      0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
172.16.0.0      *               255.255.0.0     U     1      0        0 eth0
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0

```

I have tried to read "man route", but I am not sure I understand what to do. I would prefer 192.168.0.1 to be the default also with both active.

---

### Post by SeijiSensei on 2012-09-26
Is the default gateway defined in the entry for eth0 in /etc/network/interfaces? Will the wifi connection always be available?  If not, you can solve the problem manually by running:

```

sudo ip route del default
sudo ip route add default via 192.168.0.1

```

once both interfaces are up and connected.

---

### Post by Anders J on 2012-10-06
Thanks, correct, works now!

---

