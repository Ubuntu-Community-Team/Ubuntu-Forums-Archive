---
title: "DHCP range operates hw?"
date: 2012-07-22
forum: Networking &amp; Wireless
---

### Post by ottosykora on 2012-07-22
I have some just basic linux DHCP question:


On most devices which do provide DHCP server, like routers, wifi routers etc, when there is a DHCP range set, let say from 30 to 60, then it will supply IP starting from 30 upwards.

I was now informed, that under normal linux, this is not the case, by default the DHCP app will start to assign IP from top down, e.g. here starting with 60, then 59  etc.

Is this really in general so?

---

### Post by SeijiSensei on 2012-07-22
From the [manual page for dhcpd.conf]("http://linux.die.net/man/5/dhcpd.conf"):

> The DHCP server generates the list of available  IP  addresses  from  a hash  table.   This means that the addresses are not sorted in any particular order, and so **it is not possible to predict the order in  which the  DHCP  server  will allocate IP addresses**.   Users of previous versions of the ISC DHCP server may have become  accustomed  to  the  DHCP server allocating  IP addresses  in  ascending  order, but this is no longer possible, and there is no way to configure  this  behavior  with version 3 of the ISC DHCP server. [emphasis mine]

So the allocated IP addresses are neither ascending nor descending but randomly selected from the available range.

---

### Post by Bucky Ball on 2012-07-22
You set the range on the router; that's it. I have four machines with static IPs set on the local machines. Static IPs on the router are off. DHCP is on, BUT it is serving between 192.168.0.190-200. That's it. There's no going down below 192.168.0.190; I haven't set it that way. There is no going down either, There is just, as mentioned previously, a random IP chosen from the available range. ;)

I have this setup so if a visitor wants to use their device it can join our network easily by having DHCP serve it an IP, else I'd need to set up static ones for every visitor if DHCP was off.

---

### Post by ottosykora on 2012-07-22
> **SeijiSensei said:**
> From the [manual page for dhcpd.conf]("http://linux.die.net/man/5/dhcpd.conf"):



So the allocated IP addresses are neither ascending nor descending but randomly selected from the available range.

OH, great thanks, this is clear now.

---

### Post by ottosykora on 2012-07-22
> **Bucky Ball said:**
> You set the range on the router; that's it. I have four machines with static IPs set on the local machines. Static IPs on the router are off. DHCP is on, BUT it is serving between 192.168.0.190-200. That's it. There's no going down below 192.168.0.190; I haven't set it that way. There is no going down either, There is just, as mentioned previously, a random IP chosen from the available range. ;)

I have this setup so if a visitor wants to use their device it can join our network easily by having DHCP serve it an IP, else I'd need to set up static ones for every visitor if DHCP was off.

well yes, what my routers and simlar gadgets do I know, I was rather up to info how a server in linux does behave exactly.

The problem is the work i have to do does not contain any kind of router or similar device, it contains just an small PC with linux on it and this does provide the DHCP and all the rest.

---

### Post by Bucky Ball on 2012-07-22
Okay, same applies. Whatever you are using to serve DHCP the principles I've outlined apply. Doesn't matter what the device is, for the purposes of this it is a DHCP server. ;)

---

