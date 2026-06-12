---
title: "[Proxy] Trasparent proxy to hide a real proxy?"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by dupa on 2013-01-04
My current configuration is

Computer A -> Proxy Server X -> Internet

I don't manage the Proxy Server X and I can't change it to become a trasparent proxy.

When people use a Trasparent proxy, they don't know they are using a proxy. 
*What I include in [[..]] is invisible to Computer B*
Computer B -> [[trasparent proxy server Y]] -> Internet

I want to do a different thing.
I want to use a Trasparent Proxy Y on a network where the only way to access internet is through Proxy Server X so that computer B will not need to know that there is a proxy.

Something like this

Computer B -> [[trasparent proxy server Y -> Proxy Server X]] -> Internet


Any idea?

---

### Post by dupa on 2013-01-07
any idea? :o

---

### Post by dupa on 2013-02-04
No ideas...

---

### Post by SeijiSensei on 2013-02-04
Maybe an iptables rule on machine Y that looks something like this:

```
iptables -t nat -A PREROUTING -p tcp -m tcp --dport 80 -j DNAT --to-destination ip.of.server.a:3128
```

That grabs outbound HTTP traffic and forwards it to the Squid port on server A.

---

