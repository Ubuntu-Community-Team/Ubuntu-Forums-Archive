---
title: "how is ubuntu package tcpproxy used"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by jamesbon on 2011-03-21
Can some one give me an  example scenario where this package can be used?
[http://packages.ubuntu.com/dapper/simpleproxy](http://packages.ubuntu.com/dapper/simpleproxy)

---

### Post by SeijiSensei on 2011-03-21
It's used to forward connections through a machine.  For instance, I forward external ports 110 and 143 on an Internet-facing machine back to a POP/IMAP server.  It's possible to do similar things with iptables, but I find it easier to use an "application-level" proxy instead.  (I use the now ancient [tcpproxy]("http://freshmeat.net/projects/tcpproxy/"), but the principle is the same.)

After reading the README in the simpleproxy source code, I might be induced to switch programs because of this:

"If you specify '-P <filename>' option simpleproxy will load list of
users from the <filename> (one per line). After this it will be
forwarding POP3 sessions only if client trying to authenificate [sic] as
this user."

I get hammered by the occasional dictionary attack against my POP server, so this is an attractive feature to me.

---

