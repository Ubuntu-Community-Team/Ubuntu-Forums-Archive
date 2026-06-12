---
title: "resolv.conf configuration"
date: 2005-03-23
forum: Networking &amp; Wireless
---

### Post by leny on 2005-03-23
hello everybody-

i am very new to ubuntu so i suppose this is quite a newbie question:

i am missing the resolv.conf file to enter the nameservers. I have set up the network configuration with ifconfig with no dhcp and everything works fine except that i can not resolve names.

any hints?

thanks in advance

---

### Post by az on 2005-03-23
sudo nano /etc/resolv.conf

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

CTRL-O
CTRL-X

---

### Post by leny on 2005-03-23
fixed :)

i had not written 'nameserver' only the IP's

thanks for your quick reply!

---

