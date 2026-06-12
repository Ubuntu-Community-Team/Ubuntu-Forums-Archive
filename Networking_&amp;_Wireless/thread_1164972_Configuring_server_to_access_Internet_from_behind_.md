---
title: "Configuring server to access Internet from behind a proxy server"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by martin.knapp on 2009-05-20
Hello.
I have an Ubuntu server set up and it all runs very nicely. I am setting up some test applications under Apache, written in PHP/MySQL, and this is all fine.

However, the one thing I can't work out how to do is to configure the server so that my PHP application (it's Drupal as a matter of interest) can access information on the Internet running through my company proxy server. In other words, the Ubuntu server has to call out through the proxy, which moreover is defined by a script file and not an IP address or port.

All the networking stuff must be working fine, because I can access the Internet fine using Firefox (which is configured for the proxy server), and the automatic software update which downloads updates through the Internet also works.

But any Drupal module I install which tries to access the Internet from the server simply doesn't work. There must be a way to configure this but I can't find it!!

Help much appreciated.

---

### Post by pro003 on 2009-05-20
Thats not easy to just put it down here, but there is nice "how to" [here]("http://tldp.org/HOWTO/Firewall-HOWTO.html")

---

### Post by martin.knapp on 2009-05-20
Trouble is that this how to, as far as I can tell, is all about setting up a firewall or a proxy server. I don't want to set one up (my site already has it), I want to find how I can tell my server (and specifically PHP) where the proxy is and how to get through it. And I don't think that this has anything about it (at least I can't find it)

---

