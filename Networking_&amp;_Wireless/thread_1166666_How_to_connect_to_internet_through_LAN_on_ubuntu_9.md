---
title: "How to connect to internet through LAN on ubuntu 9.04"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Yashpal1985 on 2009-05-21
Can any one help me out in connecting to internet by using wired network....on ubuntu 9.04

---

### Post by helgman on 2009-05-22
Might need some more input here, else the quick and dirty is "use a network cable". ;)

Could you be a bit more specific about the problem?

Regards,
Helgman

---

### Post by Iowan on 2009-05-22
Some of the specifics would be: 
Is machine set up for static IP or does (should) it get address via DHCP?
Post results of **ifconfig -a**.
If machine shows no IP address, post results of **lshw -C network**.
If machine has IP address, is it 169.254.X.X (avahi assigns this one).

---

### Post by dying4004 on 2009-05-23
what steps to follo if i want to setup an internet connection with static ip in ubuntu 9.04?

i did setup with network connection manager but after entering the ip and dns and gateway it doesnt show its connected.

---

### Post by Iowan on 2009-05-23
When my DHCP failed, I first set up a static address in */etc/network/interfaces* and put my DNS servers in /etc/resolv.conf.  That worked, but then I commented out the entries and set up a static address in Network Manager. As I recall, it took a couple of tries to get the info to "stick" for netmask or gateway.  I don't think running **/etc/init.d/networking restart** did much, but I didn't try **/etc/init.d/NetworkManager restart** - I just rebooted.

---

