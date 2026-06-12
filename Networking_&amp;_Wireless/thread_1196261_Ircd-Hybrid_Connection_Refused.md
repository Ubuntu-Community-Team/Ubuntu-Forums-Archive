---
title: "Ircd-Hybrid Connection Refused"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by acamela on 2009-06-24
[INDENT][/INDENT]I am trying to setup an irc chat server using ircd-hybrid. When I try to connect to my server I get the connection refused message. Previously, after messing with the iptables and /etc/ircd-hybrid/ircd.conf file, I was spontaneously able to get it to work without getting connection refused. Unfortunately, I didn't know you had to save the iptables and the power went out at my house and I lost the configuration.

I want to be able to enter my computer's local network ip (10.0.1.6) and access it on port 6667 and have irc work. Can someone please send me a working .conf file with my ip entered where it should be and iptables chain that would work for me so that I can copy it and have it work as well or possibly just a solution other than that?

Thank you so much!

I am running ubuntu server 9.04 edition on an old dell and I am hopefully going to use it as a headless server once it is fully configured. Thanks again.

---

### Post by acamela on 2009-06-24
anyone?

---

### Post by acamela on 2009-06-24
bump

---

### Post by hellmitre on 2010-09-30
I'm getting the same problem -- try to log into the server from another machine on your local network. Apparently ircd-hybrid blocks its own IP address from connecting.

---

### Post by tdiaz on 2010-11-01
Well, I can login to my own, from the same machine with irssi installed. I just can't figure out how to get past the errors with hybserv not connecting to ircd-hybrid

---

