---
title: "Networking problem"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by freeburn on 2009-12-11
I'm describing the scenario. plz help me with this.

In our office we have set up a private network. a central dhcp server
assigns private Ip's to all the Desktops. Now recently we are developing
an automated sms application. so we have made a wired connection with a
local operators smpp server. they gave us an ip and port that should be
used to get connectivity.

Now we want to use a machine which will be connected with the smpp
server and also connected with the office network for accessing our
remote content server(where our website is hosted). I have tried to use
two ethernate cards. but then the machine has two ip adresses one from
dhcp server of our office and another for smpp server.my networking
knowledge is zero. i know this question does not qualify for this
mailing list, but linux community was always helpful to me so i thought
they will help me out off the record:D

---

### Post by gordintoronto on 2009-12-11
Of course your question belongs in this forum!

You have described the situation nicely, but you haven't said anything about a problem.  What problem do you observe?

---

### Post by Iowan on 2009-12-11
I'm not familiar with **sms** or **smpp**, so my questions may be irrelevant. Is the machine with the two NIC's an Ubuntu machine (or at least Linux)?

---

### Post by freeburn on 2009-12-11
my problem is Machine gets connectivity with the office network and hence internet access is possible. but then i loose connectivity with the smpp server. i can't connect with it by telnet. the connection from the operator's smpp server is a VPN connection. that means it refuses connection from other ips other than which was assigned for us.

---

### Post by freeburn on 2009-12-11
> **Iowan said:**
> I'm not familiar with **sms** or **smpp**, so my questions may be irrelevant. Is the machine with the two NIC's an Ubuntu machine (or at least Linux)?

do i sound like a micro$hit user?:D:D

The machine in question runs on Karmic server

---

### Post by Iowan on 2009-12-11
A server setup *should* be pretty straight forward for multiple NICs. Post your */etc/network/interfaces* and the output of **ifconfig -a**

---

