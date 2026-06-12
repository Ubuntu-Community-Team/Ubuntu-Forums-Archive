---
title: "ZyXEL Wireless N Access Point as repeater"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by angelsneverdie on 2011-03-10
and I come crawling back to the ubuntu community for help.  I just got a zyxel wireless n access point to use as a repeater for my home wifi.  problem is, i have no idea how to get this thing set up.

the comments on the amazon page suggest that i need to set my computer to a static ip in order to access the config screen of the access point, but so far i've been unable to do that.

i followed the terminal instructions from this page: 
[http://www.jonathanmoeller.com/screed/?p=1669](http://www.jonathanmoeller.com/screed/?p=1669)

with no luck.  

has anyone set this up before or know how to do it?  i'd really appreciate some help.

thanks!

---

### Post by angelsneverdie on 2011-03-10
ok, so after another few hours i managed to get into the config screen.  i'm at work now, so will have to wait till i get home this afternoon to see if it is working as a repeater.  i had to edit the /etc/network/interfaces file to this:

auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
network 192.168.1.2
broadcast 192.168.1.255
gateway 192.168.1.1

i left the /etc/resolv.conf blank.

did not work after sudo ifub eth0, so i restarted computer and then it worked!

hopefully this will help other noobs like me who may run into this problem.

---

