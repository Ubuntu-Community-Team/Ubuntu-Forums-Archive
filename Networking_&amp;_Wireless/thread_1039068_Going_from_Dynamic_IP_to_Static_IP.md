---
title: "Going from Dynamic IP to Static IP"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by setsanto on 2009-01-14
Hi,

I'm trying to go from my current dynamic ip to a static ip.  I have all the name server info and all, but it doesn't seem to work.  I dual-boot, so when I type in "ipconfig /all", it returns with we having an ip address starting with 192, if, on ubuntu I go to check my ip online, it returns with an ip of 72.something.  If I try and set my address in the network interfaces file as the 72. something, my internet doesn't work.  If I set it as the 192.something, it does work, but my ip clearly isn't static.  Anyone know why?

~Setsanto

---

### Post by superprash2003 on 2009-01-14
192.x.x.x is your Local ip address which is only accessible in your LAN.. 72.x.x.x is your public ip which through which your pc can be accessed from the internet.. so they are two different levels...if your looking to make 72.x.x.x static you might need to contact your ISP for this and request them for a static ip..

---

### Post by Iowan on 2009-01-14
How do you connect to internet - router, modem, direct (probably not)?  Whatever is between your computer and the internet is *probably* acting as DHCP server, so it has the 72.x.x.x address on one port and has another on the 192.x.x.x (probably 192.168.X.1) through which it issues your computer an address.

---

### Post by setsanto on 2009-01-14
alright, so just editing /etc/network/interfaces isn't enough?

~Setsanto

---

### Post by Iowan on 2009-01-14
Probably not... Depending on why you need the static address, you may need to consider a service like dyndns or no-ip - or paying extra for one.  Several Ubuntu'ers have personal web servers using the aforementioned services.
What do you have in mind?

---

