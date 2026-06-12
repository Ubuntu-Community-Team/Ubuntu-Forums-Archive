---
title: "How to open ports 6112-6119"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by johndoughy on 2010-04-16
I need to ensure ports 6112 through 6119 are open.

I tried using Firestarter to do this, but when I search for what ports are open, it says none of them are.

I use Ubuntu 9.04.

HELP!

---

### Post by gzarkadas on 2010-04-16
If I remember well, a standard ubuntu installation has by default all ports close. So I believe it is normal that you did not see anything in firestarter - although I do not use it (and thus can't be sure) - unless you have already configured server software in your box.

This snippet will list your iptables rules (the <...> part must be filled by you, its your account name) in a file `ipt-rules' inside your home directory. Attach the file or copy its contents in your message, to figure out where you should put your allow commands.

```

sudo -i
iptables --list-rules > /home/<account>/ipt-rules
chown <account>:<account> /home/<account>/ipt-rules
exit

```Tell me also for what protocol(s) you want your ports to be open; there is no need (and is not generally advised) to be open for all.

---

