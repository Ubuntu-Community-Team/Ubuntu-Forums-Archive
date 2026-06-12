---
title: "Multiple ISP accounts with pppoeconf ?"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by ddastoor on 2009-03-05
Hi, 
I successfully got on to the net using pppoeconf with say username abc. ifconfig make a ppp0 entry. If that's the case, why do I have to run "pon dsl-provider" and not "pon ppp0" ?
So, generally, how do I run pppoeconf to make 2 accounts with my ISP? and use them when I chose to without re-running pppoeconf?

Thanks, 
Dinshaw

---

### Post by ddastoor on 2009-03-08
Ok I guess this was trivial enough.

pppoeconf makes changes to the dsl-provider file in /etc/ppp/peers
I simply ran pppoeconf with my first account and then renamed dsl-provider to <acct1> and then ran pppoeconf again with the other account and renamed dsl-provider with <account2>

pon <account1> or <account2> work

Maybe you should softlink dsl-provider to some default one.
like: ln -s <account1 or 2> dsl-provider

THanks, Dinshaw

---

