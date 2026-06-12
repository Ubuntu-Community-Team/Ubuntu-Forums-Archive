---
title: "fetchmail ::1/25 connection refused"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by phekdra on 2009-11-11
Hello all, I'm having an issue with fetchmail fetching mail and forwarding it to exim on port 25. I get the following error:

```
connection to localhost:smtp [::1/25] failed: Connection refused.
 not flushed
```

Now immediately after this it tries to connection to 127.0.0.1 and succeeds, so I'm not losing mail, but every time this happens I get a cron message informing me of the problem so I'd like to solve it.

This is a clean install of Karmic with just a few changes to add cron-ning of fetchmail and setting up my wireless card. I can telnet to port 25 on localhost and get access to exim, but if I try telnetting or pinging or anything to ::1 or ::1/25 or ::1 25 I get:

ping: unknown host ::1

Now, my hosts file looks like this:

```
127.0.0.1	localhost
127.0.1.1	bane

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Also, my loopback address says:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host

```

suggesting I have ipv6 enabled, which I thought was the default with 9.10. Can anyone please shed any light? I've seen a few people with similar problems related to fetchmail and ipv6, but I've yet to see a solution.

Andrew

---

### Post by phekdra on 2009-11-12
Well, I fixed it. Turns out I didn't have exim listening on ::1, only 127.0.0.1. A change to update-exim4.conf.conf and everything is rosy again. :D

Andrew

---

### Post by Riverside on 2010-02-11
> **phekdra said:**
> Well, I fixed it. Turns out I didn't have exim listening on ::1, only 127.0.0.1. A change to update-exim4.conf.conf and everything is rosy again. :D

AndrewI have just encountered this issue also and it took a few hours to work out!  My workaround is the same as yours, albeit that I didn't manually edit /etc/exim4/update-exim4.conf.conf but instead ran:

```
sudo dpkg-reconfigure exim4-config
```

Adding ::1 as an IP address to listen on for incoming SMTP connections in the text entry box of the relevant screen.

---

