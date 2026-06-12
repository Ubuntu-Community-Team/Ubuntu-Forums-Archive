---
title: "Cannot access internet after update"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by piprog on 2009-03-11
I have Ubuntu 8.10 (Hungarian) installed. It has been working excellent for many months, but after a recent update the Internet connection just stopped working, i.e. I can browse the LAN so the hardware should be OK, but can't access web sites, send/receive email, etc. I did not change any settings. Any idea what could go wrong?

BTW it seems I cannot ping other machines or the router either.

TIA

---

### Post by Iowan on 2009-03-11
DNS settings intact (/etc/resolv.conf)? You can browse the network, but cannot ping it? Machine has IP address? Is it in same subnet?

---

### Post by piprog on 2009-03-12
Iowan thanks for the reply!

My router is 192.168.2.1
/etc/resolv.conf is "nameserver 192.168.2.1"
eth0 is dhcp and gets ip192.168.2.101/bcast192.168.2.255/mask255.255.255.0

with Places/Network I can access shared SMB folders on the network

my IP can be pinged form other machines
my machine name cannot be pinged from other machines

I can't ping other machines either by ip or name

---

### Post by piprog on 2009-03-13
Now I might have the solution (fingers crossed...)

In final desperation went into the router DHCP Client List and "Release"d the IP of the Ubuntu machine, then did a restart on the Ubuntu machine, and now I have ping and internet access...

Now I feel like a witch doctor :-)

---

### Post by piprog on 2009-03-13
It is strange, though, that I still can't ping the machine by name, although I can ping other machines by name...

Pinging by IP works.

Pinging other machines from this one by name does not work either

---

