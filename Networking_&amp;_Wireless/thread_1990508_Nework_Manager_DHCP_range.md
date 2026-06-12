---
title: "Nework Manager DHCP range"
date: 2012-05-29
forum: Networking &amp; Wireless
---

### Post by jwsicomputing on 2012-05-29
Hi there,

My current set up is:
Modem to ubuntu machine - ethernet port set to dhcp then i have set my other ethernet port to 'shared to other computers' which then attaches to a switch and then other devices

(both ipv6's on ubuntu ethernets set to ignore) 

All is working great. Only problem is that the machines that aquire the IP'S from ubuntu all are in the 10.42.0.x subnet, is it possible to change the DHCP range/subnet to something different as many of my clients are set to static ip's on 10.42.43.x please help!!!

Many Thanks,
James

---

### Post by Iowan on 2012-05-29
Does your machine use **dnsmasq**?

---

### Post by jwsicomputing on 2012-05-30
It uses dnsmasq-base not dnsmasq.
Should I be using dnsmasq instead???

---

