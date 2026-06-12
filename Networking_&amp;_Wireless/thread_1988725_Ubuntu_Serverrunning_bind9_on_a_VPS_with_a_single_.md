---
title: "Ubuntu Server:running bind9 on a VPS with a single nic"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by Pastalero on 2012-05-28
I hope this is the right place for this question so here it goes:
What I am attempting to do is configure Bind9 to run on a single VPS server that has only one interface eth0 and that interface is configured with the static IP address of the server.
After a lot of trial and error I have not succeeded with setting up a working vlan on the eth0 interface and I'm not sure if its a matter of forwarding the packets or if a VLAN is inappropriate for this purpose.

              Thanks for your help

---

### Post by kmyram on 2012-05-28
> **Pastalero said:**
> ...I'm not sure if its a matter of forwarding the packets or if a VLAN is inappropriate for this purpose.

What do you want to achieve? Bind doesn't need vlan to run :)
Set Bind to listen to localhost if you don't want to serve external requests.

/Kasper

---

### Post by Pastalero on 2012-05-28
I needed to set up a resolving nameserver but I am limited to the eth0/wan interface. So in that case all I need to do is configure the reverse address to 127.0.0.1 ie localhost? Oof Is it possible I have been over thinking this?

---

### Post by kmyram on 2012-05-28
> **Pastalero said:**
> So in that case all I need to do is configure the reverse address to 127.0.0.1 ie localhost?

Yup. Then your DNS only answers local requests.

/Kasper

---

### Post by Pastalero on 2012-05-28
oops I had a slip of the tounge, I meant an Authoritative Nameserve

---

### Post by kmyram on 2012-05-28
> **Pastalero said:**
> oops I had a slip of the tounge, I meant an Authoritative Nameserve

That's ok but not really related to getting Bind to run (as such) - authorative is more a kind of prioritization of DNS'
Have to ask again, then... is your nameserver going to be public?

/Kasper

---

### Post by Pastalero on 2012-05-28
Yes it will,am I right to be using ipaliases? If so should my gateway for the respective iface be my WAN address?

---

### Post by kmyram on 2012-05-28
> **Pastalero said:**
> Yes it will,am I right to be using ipaliases? If so should my gateway for the respective iface be my WAN address?

I've never heard of a multi-IP VPS that didn't come with factory setup nic's... Sorry to say, but what you're trying to achieve eludes me. Why can't you use the existing ip/nic with Bind?

/Kasper

---

