---
title: "iptables question: --dports option and context"
date: 2012-04-21
forum: Networking &amp; Wireless
---

### Post by Johnny-Gear on 2012-04-21
Hi All,

Hoping someone has a little more experience with iptables than I - shouldn't be too hard.

I am just wondering if anyone can confirm whether or not the --dports option only works in some contexts or whether it can be used in place of the usual --dport option as a valid way to consolidate many rules into single multi-port rules.

eg.

iptables -A INPUT -p tcp -m tcp --dports 135,137,138,139 -m recent --name portscan --set -j DROP

Thanks,

Johnny

---

### Post by newbie-user on 2012-04-21
Yes, you can specify multiple ports like that using --dports. It's in the man pages around line 890.

---

### Post by Johnny-Gear on 2012-04-21
> **Johnny-Gear said:**
> Hi All,

Hoping someone has a little more experience with iptables than I - shouldn't be too hard.

I am just wondering if anyone can confirm whether or not the --dports option only works in some contexts or whether it can be used in place of the usual --dport option as a valid way to consolidate many rules into single multi-port rules.

eg.

iptables -A INPUT -p tcp -m tcp --dports 135,137,138,139 -m recent --name portscan --set -j DROP

Thanks,

Johnny

After doing some further reading I have come to the conclusion that the right way to construct a multi port rule such as mine is as follows:

RANGE:

iptables -A INPUT -p tcp -m multiport --dports 135:139 -m recent --name portscan --set -j DROP

INDUVIDUAL PORTS:

iptables -A INPUT -p tcp -m multiport --dports 135,136,137,138,139 -m recent --name portscan --set -j DROP

Thanks for the help everyone.

Regards,

Johnny

---

