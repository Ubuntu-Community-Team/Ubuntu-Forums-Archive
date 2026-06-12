---
title: "MediaTomb Deamon"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by dema on 2008-03-28
I'm trying to get mediatomb deamon working. I've changes NO_START from "yes" to "" in /etc/default/mediatomb.
Because my laptop are running on wireless network, I also changes to INTERFACE="eth1".

But when I startup my laptop I can't see my mediatomb on my PS3. Is it because my laptop doesn't have network connection when starting mediatomb?

If I manually run mediatomb from the terminal everything works - but I would like it to start itself.

I hope somebody can help me to get mediatomb deamon working :)

---

### Post by dema on 2008-03-28
Well. I tried to remove the content from the mediatomb.html.
Everytime mediatomb starts it will update this file with the location for the webadmin - eg. 192.168.1.33:49152

But after removing the content from the file and rebooting my system, there are still no content in this file. This tells me that mediatomb doesn't start.

Here you see med /etc/default/mediatomb file:

```
# Defaults for MediaTomb initscript
# sourced by /etc/init.d/mediatomb
# installed at /etc/default/mediatomb by the maintainer scripts

#
# This is a POSIX shell fragment
#

# Set whether the daemon should be started. Set this value to anything
# but 'yes' to enable the daemon
NO_START=""

# Additional options that are passed to the daemon.
OPTIONS=""

# The network interface for MediaTomb to bind to and for which the multicast 
# routing entry should be added; "" if the route shouldn't be added at all.
# For example: INTERFACE="eth0"
INTERFACE="eth1"

# The route command and arguments to be used if INTERFACE is defined.
# These variables should normally be left unmodified.
ROUTE_ADD="/sbin/route add -net 239.0.0.0 netmask 255.0.0.0"
ROUTE_DEL="/sbin/route del -net 239.0.0.0 netmask 255.0.0.0"

# The user and group that MediaTomb should be run as.
USER="mediatomb"
GROUP="mediatomb"
```

Can anybody tell me, why mediatomb doesn't start as deamon?

---

### Post by dema on 2008-03-28
And another test:

Again I remove the content from mediatomb.html og starts the mediatomb from init.d:
```
sudo /etc/init.d/mediatomb start
 * Starting upnp media server mediatomb                                  [ OK ]
```

But still no content in the .html-file!

My mediatomb only works, if I starts it manually from the terminal :(

---

### Post by jethro10 on 2008-04-12
I've just spent about 4 hours on this as well.
The answer came from a bug report on Ubuntu's launchpad entry for mediatomb.

edit the interfaces file eg,

gksudo gedit /etc/network/interfaces

and add this for the interface, its most likely missing

[B]auto eth0
iface eth0 inet dhcp[/B]

If you add the network monitor applet and click it once installed, it will tell you the name of the connection. mine was eth0 and most (all?)  wired cards will be the same.

hope it helps
Jeff

---

### Post by StevenHarper on 2008-04-12
I have raised a bug about this about 7 days ago

[https://bugs.edge.launchpad.net/ubuntu/+source/mediatomb/+bug/212441](https://bugs.edge.launchpad.net/ubuntu/+source/mediatomb/+bug/212441)

Steve

---

### Post by wilko10 on 2008-04-13
> **StevenHarper said:**
> I have raised a bug about this about 7 days ago

[https://bugs.edge.launchpad.net/ubuntu/+source/mediatomb/+bug/212441](https://bugs.edge.launchpad.net/ubuntu/+source/mediatomb/+bug/212441)

Steve

That was you?

Thanks it really helped.
J

---

### Post by dema on 2008-04-13
What if I use wireless network? eth1

---

### Post by jethro10 on 2008-04-15
> **dema said:**
> What if I use wireless network? eth1

Have you just tried replacing eth0 with eth1 ?

---

