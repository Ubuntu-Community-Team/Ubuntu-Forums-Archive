---
title: "I need to change my ip address"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by thebrandon on 2012-02-27
I installed Openwrt on my router and it crashed and now I have to attempt to access it in failsafe mode  [http://wiki.openwrt.org/doc/howto/generic.failsafe](http://wiki.openwrt.org/doc/howto/generic.failsafe)
But to do that I need to "Set your computer's IP to 192.168.1.2, subnet 255.255.255.0" what I did was change my /etc/networking/interfaces to look like this :

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0

But Im still not able to access the router and I know very little about networking and I dont want to mess anything up that I cant fix!

---

### Post by azmyth on 2012-02-28
Not sure if it's needed but mine has a gateway. Also, I assume you have typo since the file should be /etc/network/interfaces

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by thebrandon on 2012-02-28
Thanks I will give it a try, I typed the location of the interfaces file from memory but I will double check it.

---

### Post by thebrandon on 2012-02-28
Well I still cant get access, also my wired connections says "device not managed"
when I ssh it gives me this :
:~$ ssh 192.168.1.1
ssh: connect to host 192.168.1.1 port 22: No route to host

---

