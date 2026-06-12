---
title: "Proxy (squid3) help. Urgent!"
date: 2012-09-25
forum: Networking &amp; Wireless
---

### Post by marjoh05 on 2012-09-25
Hello, im a ICT apprentice at a school.

I have been working a little on ubuntu server the past year, and i start to get used to it. But my network knowledge is the problem.

We are making a exam/test-room.

In this room we have about 30 imacs with its own Vlan.

The studens will only have access to some sites to deliver their tasks / exam.

I have setup my squid with "whitelist" and cant get it to work because of network configurations.

I have 2 network ports, ETH0 will be network inn from "the internet" and ETH1 will be network out to to the switch.
Can i do it that way at all, or can i just plug the server to the svitsj and make the traffic go trought it, how?

When im an apprentice you may think my leader should teach me this, but he has a "parent vacations" because of his newborn kid.

Regards
Marjoh05

---

### Post by marjoh05 on 2012-09-25
Any one who can help a lost apprentice?

Everything helps :)

Regards Marjoh05

---

### Post by SlugSlug on 2012-09-25
You might find ipcop easier

[http://www.ipcop.org/docs.php](http://www.ipcop.org/docs.php)

---

### Post by marjoh05 on 2012-09-25
Thank you.

Do i connect this firewall to the switch and force the traffic true it, or do i plug it in between between internet and the svitsj?

---

### Post by SlugSlug on 2012-09-25
read docs on ipcop.

You will have ETH0 connected to internet (nothing else connects direct to internet)

and ETH1 connected to LAN switch

---

### Post by marjoh05 on 2012-09-25
Thank you, i will check it out. Do you mind if i send you some PMs with simple quiestions if i get stuck? (I will not overwhelm you with hard / long task ofcourse)

and just one more question before i start, when i have configured it, can i plug ETH1 into my laptop to check if it works, or do i need a router / switch?

---

### Post by SlugSlug on 2012-09-25
You'll need a switch

Sure you can PM but your better posting here so others can advise or if someone else has the same question they can follow the thread

---

### Post by marjoh05 on 2012-09-25
Thank you! I agree, i better post here.

---

### Post by marjoh05 on 2012-09-25
Does this look right to you?

auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1


auto eth1
iface eth1 inet static
        address 192.168.0.100
        netmask 255.255.255.0

Im using a _dumb_ switch from ETH1 to computer

Edit: wrote switch in Norwegian, sorry :)

---

### Post by SlugSlug on 2012-09-25
no eth0 and eth1 need to be on different networks

make eth1 192.168.1.1

---

