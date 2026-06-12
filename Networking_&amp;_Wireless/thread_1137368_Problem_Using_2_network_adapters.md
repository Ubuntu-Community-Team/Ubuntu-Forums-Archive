---
title: "Problem Using 2 network adapters"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by syntheticflag on 2009-04-25
I have integrated ethernet, and a PCI W/Lan card in my PC (AMD Sepmron 3500+, 1.5 GB RAM, Intrepid Ibex now upgrading to 9.04 as I post) and have my w/lan enabled. Would like to keep the w/lan enabled for my internet connection, and run an ethernet crossover cable to another PC to access files on the pther computer.
Every time I enable my autoeth0, my wlan looses it connection to the internet, but when I re-enable the wlan the autoeth0 disables? Keep in mind I am trying to do this with a crossover cable (no router), but can put a router between them if neccesary. Any Ideas?
The other PC is an Intel p4 1GB Ram, Intrepid Ibex 8.10, and also has a w/lan and integrated ethernet.
syntheticflag is online now Report Post   	Edit/Delete Message

---

### Post by cariboo on 2009-04-26
In order to use both network interfaces, they need to be on different netblocks, if wireless ap address is 192.168.1.100 the wired interface should be 192.168.0.100. In order for what you to do what you want you will probably have to set your wired with a static ip address:

edit /etc/network/interfaces to look aomething like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address    182.168.1.100
netmask     255.255.255.0
network     192.168.1.0
broadcast     192.168.1.255
gateway     192.168.1.1

```

all ip addresses are just examples.

---

