---
title: "simple UDP port forwarding?"
date: 2011-01-30
forum: Networking &amp; Wireless
---

### Post by akos.maroy on 2011-01-30
I'm trying to set up very simple UDP port forwarding, but can't seem to have good results. I read trough netcat and iptables manuals, but can't seem to figure things out.

my setup is the following:

I have machine1, listening on UDP port 49000.
I have machine_fw, which accepts connections on 59000, and forwards all this to machine1:49000 (and returning traffic too)
I have machine2, which will connect to machine_fw:59000, and this way communicate at the end with machine1:49000, as machine_fw is taking care of forwarding

is there an easy way to achieve this?

---

### Post by SeijiSensei on 2011-01-30
I've used [uproxy]("http://freshmeat.net/projects/uproxy") once in a while.

---

### Post by akos.maroy on 2011-01-30
> **SeijiSensei said:**
> I've used [uproxy]("http://freshmeat.net/projects/uproxy") once in a while.

thanks - looks good..

---

