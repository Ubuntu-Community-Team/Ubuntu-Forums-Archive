---
title: "static IP problem"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by ZMarre on 2006-04-25
Hi all,

I want to set up my ubuntu install using a static IP. When using DCHP at home, everything works fine.

I did following things:

° in my /etc/network/interfaces I did set the dhcp-line (iface eth0 inet dhcp) in comment and added the following code:

adress 172.10.100.101
netmask 255.255.0.0/16
gateway 172.10.0.2
dns-nameservers 10.60.64.7

-> didn't work, pinging google did show me 'host not found' and pinging my DNS showed 'network unreachable'.

ifconfig only shows eth0, so my loopback seems suddenly disappeared?!

° then I added in the /etc/resolv.conf the line 'nameserver 10.60.64.7'

-> didn't seem to be a solution

° in /etc/dhcp3/dhclient.conf I added the line 'prepend domain-servers 10.60.64.7'

-> no step forward

° I tried to add a route to the gateway by using the command 'route add -host 172.10.0.2 netmask 255.255.0.0 eth0'

-> error '255.255.0.0: host name lookup failure'

I also tried to bring my lo back by using the command 'route add 127.0.0.0' but that also didn't help a damn thing.

The first who can help me out of this friggin' situation I buy a good Belgian beer! ;)

---

### Post by tribaal on 2006-04-25
Hi there. 

Well... I got intrigued by your problem, because it seemed so obscure, and came up with an answer:

Hopefully, it's *very* easy to do: in GNOME, just go 
Applications > System tools > Networking tools

After your sudo password, you should be able to access the "peripherals" tab, where your network card should be listed. 
Now press "configure", and you should be now able to switch the "configuration" box to "static IP", and then just fill the fields :)

This worked out like a charm for me, I hope it'll be as helpful for you ;)

By the way, my Ubuntu is in French, so labels and options might be called something a bit different from what I point you...

Cheers

- trib'

---

### Post by ZMarre on 2006-04-25
thx already, but I'm using the server install, so no X installed ;)

---

### Post by alamba on 2006-04-25
Can you change back your interface file to its original state? Once you do that, execute the following:

#ifconfig eth0 172.10.100.101 mask 255.255.0.0 gw 172.10.0.2
#route add default gw 172.10.0.2

Post the following if it doesn't work:
1. ifconfig
2. netstat -rn
3. cat /etc/resolv.conf
4. ping 172.10.0.2
5. ping 4.2.2.2
6. ping oracle.com

A

---

### Post by tribaal on 2006-04-25
> thx already, but I'm using the server install, so no X installed

Ah rats, for once I thought I could be helpful :)

---

### Post by Iowan on 2006-04-25
Borrowed from another post:
```
# The primary network interface
iface eth0 inet static
address 206.144.0.6
netmask 255.255.255.240
network 206.144.0.0
broadcast 206.144.0.15
gateway 206.144.0.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 60.0.15.12
dns-search att.serverpath.net
```
Some differences from yours - the **iface** line has **static**,
**adress** is spelled **address**

---

### Post by ZMarre on 2006-04-26
[QUOTE=Iowan]Some differences from yours - 
**adress** is spelled **address**[/QUOTE]

Call Chuck Norris to roundhousekick me! ](*,) 

If you come over to Brussels, Belgium I'll buy you a complete crate of belgian beer! ;) 

Thx all :KS , this thread can be locked.

---

