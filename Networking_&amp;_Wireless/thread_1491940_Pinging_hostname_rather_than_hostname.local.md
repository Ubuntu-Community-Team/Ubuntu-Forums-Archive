---
title: "Pinging hostname rather than hostname.local"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by riksweeney on 2010-05-24
Hi,

I'm trying to ping another Ubuntu computer on my local network. If I try doing,

ping <hostname>

then I get the message

ping: unknown host <hostname>

however, if I do

ping <hostname>.local

then I get a response back. I was wondering how I can change it so that I can ping without having to append .local

I've installed winbind and modified my /etc/nsswitch.conf file but this has made no difference.

Thanks

Richard

---

### Post by Iowan on 2010-05-24
I have DNSMasq as DHCP/DNS server on my network - it seems to work. Avahi uses the .local suffix - my (very limited) experience with **avahi** hasn't left me with a good feeling...

---

### Post by Yankees9920 on 2011-05-15
I'm having the same issue and would prefer not to run my own DNS server though.
For me its .home instead of .local
Additionally what seems to happen for me is that I have to type hostname.home the first time I connect, after that just hostname works.

---

