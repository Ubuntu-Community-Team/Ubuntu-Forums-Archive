---
title: "tricky network share folder question"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by nephish on 2006-06-27
hello there,
i have four computers i am trying to network together. so heres the deal.
i get dsl from my isp that goes to my main box eth0
then i have firestarter, iptables, etc share internet via eth1
eth1 goes to a switch. from that switch, internet goes to other three computers, and also a wireless router. (so i can occationally use me laptop).
Since one of the computers is in the opposite room of the house, i want to put in a wireless card so it gets internet from the wireless router too. The other three computers have a static ip. Every computer has rw access to one nfs folder on a computer inside the LAN.

so, i guess i need a soulution here about allowing the wireless connected computer(s) get to the shared folder. The deal is, wont every computer behind the wireless router appear to have the same ip address ? i dont want anyone driving by with a laptop to have access to my shared stuff.

what is a good idea here ?

some config stuff -

main computer (router) eth1 192.168.1.1 ( serves as the gateway )
sharing computer 192.168.1.2
another box 192.168.1.3
and then the wireless router --- ?????

the wireless router serves out a different range of ips. like 10.10.10.125 etc...

any good ideas here ? do i need to move the shared folder to the main router computer ?
thanks

---

### Post by AndyCat on 2007-07-18
Are u using your computer as a Gateway or the router instead?
I have a similar net configuration here.
5 computers all of them using linux, 2 of them using XP for some programs.
I have DSL as well but my modem is connected to my wireless router not to my computer.
Set samba and Voila everything worked....

---

