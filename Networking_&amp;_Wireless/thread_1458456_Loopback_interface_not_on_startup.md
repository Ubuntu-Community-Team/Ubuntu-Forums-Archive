---
title: "Loopback interface not on startup"
date: 2010-04-20
forum: Networking &amp; Wireless
---

### Post by gbetous on 2010-04-20
Hi !

I own an Ubuntu Server 9.04 on a remote dedicated server. Since a few days (?) the loopback interface is not 'up' on reboot : I only have eth0 (which works fine).

Here is my /etc/networking/interfaces (did not change since server initialization):

---------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#eth0 is enabled by initrd
auto eth0:0
iface eth0:0 inet static
        address xx.xx.xx.xx (censured)
        netmask 255.255.255.255
---------------------------

As root, I only have to do a 'ifconfig lo up' to make it work.

Does anybody have any idea why this interface does not show up on boot ?

Regards,

Guillaume

---

### Post by gbetous on 2010-04-21
Nobody ?

---

### Post by Iowan on 2010-04-21
I presume that's */etc/network/interfaces*.
Nothing really obvious jumps out as a problem.

---

### Post by gbetous on 2010-04-24
Thank you for your reply.

Ok, so I'll add a "ifconfig lo up" in /etc/rc.local

Can you confirm that it is the right place to put this command ?

---

