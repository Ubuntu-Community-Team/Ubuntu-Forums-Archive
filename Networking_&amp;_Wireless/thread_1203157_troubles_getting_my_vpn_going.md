---
title: "troubles getting my vpn going"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by reggler on 2009-07-03
Hi,

I would like to connect to my office's M$ VPN.
I configured it all following [https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)
But when i try to connect i get:"VPN connection failed" and syslog tells me the following:
```
Jul  2 21:54:19 reg-laptop pppd[21899]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Jul  2 21:54:19 reg-laptop pppd[21899]: pppd 2.4.5 started by root, uid 0
Jul  2 21:54:19 reg-laptop pppd[21899]: Using interface ppp0
Jul  2 21:54:19 reg-laptop pppd[21899]: Connect: ppp0 <--> /dev/pts/1
Jul  2 21:54:20 reg-laptop pppd[21899]: Modem hangup
Jul  2 21:54:20 reg-laptop pppd[21899]: Connection terminated.
Jul  2 21:54:20 reg-laptop pppd[21899]: Exit.
```


Why is that? Can anyone help me?

Thank you!
Ron

---

### Post by reggler on 2009-07-07
no one able to help me here? :o is vpn for all of you "just working"? :o

---

### Post by PGScooter on 2009-07-07
> **reggler said:**
> no one able to help me here? :o is vpn for all of you "just working"? :o

No, you're not alone. I have had a lot of trouble trying to connect to my University's account with VPN.

---

### Post by PGScooter on 2009-07-07
reggler,

I'm guessing you've thought of this, but thought I'd give it a shot. Are you sure that your firewall, your modem's firewall, or your IP service is not blocking VPN connections? Have you tried it on windows?

---

### Post by reggler on 2009-07-07
> **PGScooter said:**
> reggler,

I'm guessing you've thought of this, but thought I'd give it a shot. Are you sure that your firewall, your modem's firewall, or your IP service is not blocking VPN connections? Have you tried it on windows?

Yes I have, works fine with my virtual machine! :o ... Weird, eh?

---

### Post by PGScooter on 2009-07-08
shoot. Well, I do think VPN support is getting better. Maybe try in a couple of years? :)

---

