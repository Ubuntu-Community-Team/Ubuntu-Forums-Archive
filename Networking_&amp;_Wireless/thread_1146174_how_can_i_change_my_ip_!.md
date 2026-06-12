---
title: "how can i change my ip ?!"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by fady-0 on 2009-05-02
how can i change my ip manually  in ubuntu :lolflag: ?!

---

### Post by _Purple_ on 2009-05-02
Right click the network icon from panel then go to edit connections.

---

### Post by llemm on 2009-05-02
> **fady-0 said:**
> how can i change my ip manually  in ubuntu :lolflag: ?!

ifconfig <network card> <Ip address you want>
Example
If your network card is eth0 and the Ip address that you want is 192.168.0.2

ifconfig eth0 192.168.0.2

if you want to add a subnet mask

ifconfig eth0 192.168.0.2 netmask 255.255.255.0

HTH

---

### Post by fady-0 on 2009-05-02
thanx it was very helpful :)

---

### Post by fady-0 on 2009-05-02
hi , i got this " permission denied " :(

---

### Post by _Purple_ on 2009-05-02
If you are using CLI, add sudo before the command.

---

### Post by Kareeser on 2009-05-02
Just a remark... the comments here talk about changing your **private** IP, which is the IP address given to you by the DHCP server on your router.

If you're looking to change your **public** IP to circumvent some blocking system such as a forum ban, then:
1. You're getting the wrong advice :)
2. According to the forum rules, we aren't allowed to help you.

---

### Post by fady-0 on 2009-05-02
nooooooooooo the story is i have ONE ip to join the network with many pcS so i wanna change my ips to be able to join the network with any pc :)

---

### Post by Iowan on 2009-05-02
A simple solution would *seem* to be installing a router between your machines and the network. The router would get the one IP.  Most routers can NAT the machines behind them and act as DHCP server, too.

---

