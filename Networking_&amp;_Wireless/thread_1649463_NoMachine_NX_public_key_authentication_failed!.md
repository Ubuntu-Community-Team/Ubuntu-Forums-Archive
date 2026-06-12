---
title: "NoMachine NX public key authentication failed!"
date: 2010-12-20
forum: Networking &amp; Wireless
---

### Post by paul260 on 2010-12-20
Hi All,

   I'm hoping for some pointers on this one - I'm seriously stuck!

I'm trying to restrict command line ssh and yet keep NoMachine working, so I followed this post [http://www.nomachine.com/ar/view.php?ar_id=AR07C00235](http://www.nomachine.com/ar/view.php?ar_id=AR07C00235) and tried adding this to /etc/ssh/sshd_config:

AllowUsers nx@*.*.*.* paul@*.*.*.* *@::ffff:127.0.0.1 *@127.0.0.1

On restarting the ssh daemon other users can't login by the terminal, but I can. However, NoMachine won't log me in. I get:

NX> 502 ERROR: Public key authentication failed

As a server side check:

$ sudo /usr/NX/bin/nxserver --usercheck paul
NX> 900 Verifying public key authentication for NX user: paul.
NX> 900 Public key authentication succeeded.
NX> 999 Bye.

And as a client side check:

$ ssh -i /usr/NX/share/keys/server.id_dsa.key nx@<my server IP>
HELLO NXSERVER - Version 3.4.0-14 - LFE
NX> 105 ^C
NX> 999 Bye.
Connection to <my server IP> closed.

I've tried replacing default ssh keys twice according to this post [http://www.nomachine.com/ar/view.php?ar_id=AR01C00126](http://www.nomachine.com/ar/view.php?ar_id=AR01C00126).

I've been careful with permissions, and even tried the suggestion on this post [http://ubuntuforums.org/showthread.php?t=941530&page=1](http://ubuntuforums.org/showthread.php?t=941530&page=1) of adding sshd: LOCAL to /etc/hosts.allow, but still no joy!

Has anyone come across this problem before, and/or know of a fix?

If it matter I'm running Xubuntu 10.10 64 bit.

Cheers All,

Paul.

---

### Post by howefield on 2010-12-20
Moved to Networking and Wireless.

---

