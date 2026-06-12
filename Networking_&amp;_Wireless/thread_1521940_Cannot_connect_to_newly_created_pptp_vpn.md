---
title: "Cannot connect to newly created pptp vpn"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by jabalsad on 2010-07-01
Hi all,

I pretty much followed the tutorial here:
[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

But when I try to connect to this vpn from my ubuntu desktop, it fails. I created a new PPTP VPN connection, typed in the username and password i put into /etc/ppp/chap-secrets, but I'm just getting "connect failed".

Is there any way to debug this issue? I'll appreciate the feedback.

Thanks.

---

### Post by jabalsad on 2010-07-01
I also know that the server is working since I can connect to it from a windows machine.

---

### Post by jonobr on 2010-07-01
Hello

Debug from this should be contained in 
/var/log/daemon.log

If you open that after a connection attempt and post here, that may help

---

