---
title: "set up static connection"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by mkeyes001 on 2010-06-23
so I've configured my /etc/network/interfaces file:

iface eth0 inet static
address x.x.x.x
netmask x.x.x.x
network x.x.x.x
broadcast x.x.x.x
gateway x.x.x.x

I would like to set up a default domain as well, I configured /etc/resolv.conf to look like this:

domain dal.design.ti.com
search dal.design.ti.com
nameserver x.x.x.x


I restarted networking with /etc/init.d/networking restart and my eth0 is not being configured on start up, what am I doing wrong?  Is there another file I'm forgetting to update somewhere?

---

### Post by georgemc on 2010-06-23
I use a static as well and my /etc/network/interfaces file looks like this:

auto eth0
iface eth0 inet static
 address x.x.x.x
 netmask x.x.x.x
 network x.x.x.x
 broadcast x.x.x.x
 gateway x.x.x.x

Make sure you have "auto eth0" in front of your settings.

Hope this helps.

George

---

### Post by mkeyes001 on 2010-06-23
when I add the auth eth0 it failes to restart the networking:

ifup: couldn't read interfaces file

???

---

### Post by Iowan on 2010-06-23
Is thread actually [SOLVED]?
Ws that a typo - or did you actually add "auth eth0" instead of "auto eth0"?

---

