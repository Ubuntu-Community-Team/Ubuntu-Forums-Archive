---
title: "Port forwarding outside LAN with iptables?"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by misha680 on 2009-02-09
Hi, I am trying to forward a port (say 399) to port 993 on imap.gmail.com as my company seems to block port 993 (no idea why). In any case, I need to use iptables and something simple like:

```

iptables -t nat -A prerouting_wan -p tcp --dport 399 -j DNAT --to 99.188.135.161:993
iptables -A forwarding_wan -p tcp --dport 993 -d 99.188.135.161 -j ACCEPT

```

does not seem to do the trick, whereas something similar with a local address works just fine. ANy hints?

Thank you
Misha

---

### Post by dmizer on 2009-02-09
Not a direct answer to your question but, your company may be purposfully blocking port 993 to prevent imap access to non-corporate email. If you have a legitimate need to access your gmail account, you should contact your network administrators.

---

### Post by misha680 on 2009-02-10
> **dmizer said:**
> Not a direct answer to your question but, your company may be purposfully blocking port 993 to prevent imap access to non-corporate email. If you have a legitimate need to access your gmail account, you should contact your network administrators.

Perhaps... but they are not blocking [www.gmail.com](www.gmail.com) HTTP so why block IMAP?

My solution:
```

## Forward 399 to imap.gmail.com port 993
GMAIL=$(nslookup imap.gmail.com | sed s/"Address 1: 127.0.0.1"// | grep Address | cut -d " " -f 3 | head -n 1)
iptables -t nat -A prerouting_rule -p tcp --dport 399 -j DNAT --to $(GMAIL):993
iptables -A forwarding_rule -p tcp --dport 993 -d $(GMAIL) -j ACCEPT
iptables -t nat -A postrouting_rule -p tcp --dport 993 -d $(GMAIL) -j MASQUERADE

```

Found help on web too

Misha

---

### Post by dmizer on 2009-02-10
> **misha680 said:**
> Perhaps... but they are not blocking [www.gmail.com](www.gmail.com) HTTP so why block IMAP?
No idea really.

> **misha680 said:**
> Found help on web too

That's what I would have had to do to offer you more support. :)

---

