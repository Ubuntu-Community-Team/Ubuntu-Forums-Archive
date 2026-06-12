---
title: "Multiple gateways on single interface"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by LWTechsupport on 2009-10-18
Hi looking for some help with networking interfaces. Basically I am trying to set 2 different gateways to the same interface with the same IP. I know how to setup up profiles, but I need everything on one profile.

Basically at work we have 2 different gateways. One for normal traffic, then one for dmz traffic. What I want to be able to do, is if a port is closed on the normal gateway. It will try and go out on the DMZ gateway.

Does anyone know if this is possible? Do I need to use something like a vlan to use the second gateway?

---

### Post by dmizer on 2009-10-18
> **LWTechsupport said:**
> Hi looking for some help with networking interfaces. Basically I am trying to set 2 different gateways to the same interface with the same IP. I know how to setup up profiles, but I need everything on one profile.

Basically at work we have 2 different gateways. One for normal traffic, then one for dmz traffic. What I want to be able to do, is if a port is closed on the normal gateway. It will try and go out on the DMZ gateway.

Does anyone know if this is possible? Do I need to use something like a vlan to use the second gateway?

How would you accomplish this in Windows?

Unless I'm way off, the only way I can think of to make that work is to set up the filtered gateway as your primary DNS server, and your DMZd gateway as your secondary DNS server.

---

### Post by LWTechsupport on 2009-10-18
The only machine I use windows on is my machine at work, :(. Thats only because my company is a Microsoft partnered comany.

I have 2 nics on my windows machine, one for internal and the other for DMZ. The only thing I use the DMZ for is certain applications like irc, and message programs. Basically it's like using route to mark a packet to use a certain nic.

Since I only have one nic on my laptop I was hoping to be able to set it be able to use 2 different gateways. If this is not possible, I will have to find some other way to use my programs.

---

### Post by dmizer on 2009-10-19
I don't know how to do it in Network-Manager (in fact, it may not be possible). But here's how it would look in /etc/network/interfaces

```
#Internal network 
auto eth0
iface eth0 inet dhcp

#DMZ network
auto eth0:1
iface eth0:1 inet dhcp
```

Basically you're creating a second virtual NIC called eth0:1.

I'll test network-manager with a spare machine when I get home.

---

### Post by dmizer on 2009-10-19
Looks like you will have to configure your second device with static settings. You WILL be able to do so without disabling network-manager however. Just add something like the following to your /etc/network/interfaces file:
```
auto eth0:1
iface eth0:1 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

You should change the above details to match the requirements of your DMZd gateway. Reboot, or run this command: sudo /etc/init.d/networking restart

After that, you should have two functional network adaptors ... both running through your single physical NIC.

---

