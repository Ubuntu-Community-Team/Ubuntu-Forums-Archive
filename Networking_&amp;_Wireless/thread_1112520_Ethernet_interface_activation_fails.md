---
title: "Ethernet interface activation fails"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by cattox on 2009-03-31
Hi,

I recently installed ubuntu 8.10 (cmd line mode) on an old machine.
It all went well till I try to activate the ethernet interface.

when I hit the command:
```
ifup eth0
```
I get:
```
/etc/network/interfaces:6 unknown method
ifup: could'n read interfaces file "etc/network/interfaces"
```

when I hit the command:
```
/etc/init.d/networking restart
```
I get:
```
* Reconfiguring network interfaces...
/etc/network/interfaces:6 unknown method
ifdown: could'n read interfaces file "etc/network/interfaces"
/etc/network/interfaces:6 unknown method
ifup: could'n read interfaces file "etc/network/interfaces"
```

my etc/network/interfaces file is the following:
```
#The loopback network interface
auto lo
iface lo inet loopBack

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

I wonder If anyone can help me with this..

thanks in advance

---

### Post by chili555 on 2009-03-31
Would you please try *sudo* in front of your commands? Please let us know.

---

### Post by cattox on 2009-03-31
Hi Chili,

thanks for the reply.

I did used sudo in the commands, I didn't write it just to simplify the post.. sory for the confusion.

Any ideas?!? :(

---

### Post by chili555 on 2009-03-31
> Any ideas?!?A few. First, I don't know if this is a typo in the file or a typo in posting it here, but I'd check and change this:```
auto lo
iface lo inet loop[COLOR="Red"]B[/COLOR]ack
```to read like this:```
auto lo
iface lo inet loopback
```This part:> /etc/network/interfaces:[COLOR="Red"]6[/COLOR] unknown methodtypically means the problem is on line 6. However, unless there are four lines of text you've omitted, line 2 looks flawed.

I might also run:```
 ls -al /etc/network/interfaces
```Make sure that 'r' for 'readable' applies to one and all, like this:```
ls -al /etc/network/interfaces
-rw-r--r-- 1 root root 319 2009-03-21 19:59 /etc/network/interfaces
```If not, please run:```
sudo chmod +r /etc/network/interfaces
```I think one of these two will fix it.

---

### Post by cattox on 2009-04-01
Great Chili!!!!

it was the typo you mentioned!! 

> loopBack -> loopback

working fine now. :guitar:

thanks!!!

---

### Post by chili555 on 2009-04-01
Terrific! Glad it's working for you.

---

