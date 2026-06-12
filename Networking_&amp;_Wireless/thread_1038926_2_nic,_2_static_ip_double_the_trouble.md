---
title: "2 nic, 2 static ip double the trouble"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by BFris on 2009-01-14
Hi I have a problem with configuring a computer with 2 nics and 2 static ips. The computer doesn't seem to know which NIC to use to talk to the internet. Both NICs are on the same subnet and have the same gateway. e.g. 
```
  eth0   192.168.0.26 \   
                       }  gateway for both 192.168.0.2
  eth1   192.168.0.25 / 
```
With both cards up, I can't reliably get communication through to the Internet. ???

More gory details:

I have 2 Kubuntu servers sitting on a Windows network. I want one of them to act as the production database server and the other to just wait until the first one breaks. Should improve my uptime, right? 

```
192.68.0.1  -- Windows proxy to Internet
192.68.0.2  -- Windows DC

192.68.0.25 -- IP for production server (could actually be 
               Kubuntu1 or Kubuntu2)

192.68.0.26 -- Kubuntu1
192.68.0.27 -- Kubuntu2
```
        
Each Kubuntu box has 2 NICs. So I thought the easiest thing would be to configure 1 NIC for the production server address and the other NIC for the server name e.g.

```
Kubuntu 1 active server    Kubuntu2 waiting as backup
-----------------------    --------------------------
auto eth0                  auto eth0
iface eth0 inet static     iface eth0 inet static
address 192.168.0.26       address 192.168.0.26
gateway 192.168.0.2        gateway 192.168.0.2
netmask 255.255.255.0      netmask 255.255.255.0 

auto eth1            
iface eth1 inet static     iface eth1 inet static
address 192.168.0.25       address 192.168.0.25
gateway 192.168.0.2        gateway 192.168.0.2
netmask 255.255.255.0      netmask 255.255.255.0
```

so Kubuntu2 will have the 192.168.0.25 address remembered, but the network card won't come up at boot.

The problem is, I can't get the production server to reliably talk to the internet. Any ideas?

---

### Post by BFris on 2009-01-14
So it looks like much of my trouble can be attributed to mixing Network Manager and ifupdown. Apparently this is a really bad idea and that's what I was doing.

For now, I'm using ifupdown and /etc/network/interfaces. 

Advantages: easy to do access via ssh. 

Disadvantages: no gui for Windoze folks if I'm not around to mess with configuration.

---

### Post by Iowan on 2009-01-14
Two NIC's in the same subnet will probably cause problems with routing.

---

