---
title: "SFTP/load-balancing/round robin help."
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Jisamaniac on 2009-12-15
Hello,

A friend and I both have SFTP Ubuntu Server 9.10 with jail chroot set up. We are using FileZilla to connect to our individual servers, but we want to combined are internet connections to have a faster upload. 

Now I'm not sure we we have to use BIND(9) round robin, set up a cluster, or get some kind of load-balancing software.

I'm looking for the easiest way because we would like to add more servers later down the road.
Any links to tutorials are appreciated. :D

JP

---

### Post by Lars Noodén on 2009-12-15
You can do the load balancing at the router or switch if you are using IP Tables on any linux (or PF on bsd).  

You'll have to look around, but these three will help get you started:

[http://linuxgazette.net/108/odonovan.html](http://linuxgazette.net/108/odonovan.html)
[http://www.damia.net/comos/balance/](http://www.damia.net/comos/balance/)
[http://www.docum.org/docum.org/faq/cache/57.html](http://www.docum.org/docum.org/faq/cache/57.html)

Also look around in the [iptables](http://manpages.ubuntu.com/manpages/karmic/en/man8/iptables.8.html) manual.  There are a lot of possibly useful options like **clusterip** 

[http://security.maruhn.com/iptables-tutorial/x8906.html](http://security.maruhn.com/iptables-tutorial/x8906.html)

---

### Post by rnldpj on 2011-03-05
[http://jackal777.wordpress.com/2011/03/05/ubuntu-10-10-bind-round-robin-howto/](http://jackal777.wordpress.com/2011/03/05/ubuntu-10-10-bind-round-robin-howto/)

---

