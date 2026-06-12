---
title: "Disconnecting: Corrupted MAC on input"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by nil0lab on 2006-06-12
I'm getting Disconnecting: Corrupted MAC on input after a bit when doing multimeg rsync-over-ssh transfers, and occasionally with ssh sessions.

First I thought it had something to do with the new support for the cardbus airlink 101 mimo xr wireless-g card I was using, but I get the same thing when using the old wireless-b builtin on my dell i8600 (ipw2100 module).

Then I tried my old tried-and-true wired SMC cardbus card (pcnet_cs) that worked great with with Debian (kernels 2.4.x thru 2.6.8) and I'm getting the same effect.

Any ideas- is this a kernel issue or an ssh issue?  Would it help to downgrade versions on either?

root@domo:~# uname -a
Linux domo 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
root@domo:~# dpkg -l|grep ssh
ii  openssh-client                         4.2p1-7ubuntu3                        Secure shell client, an rlogin/rsh/rcp repla

---

### Post by nil0lab on 2006-06-12
Doh- silly forum software substituted a smiley icon for 8-paren above.  I think my wired card worked well with Debian-supplied kernels through 2.6.8.  Wireless-g card and builtin wireless-b didn't work at all with Debian-supplied kernels.

---

