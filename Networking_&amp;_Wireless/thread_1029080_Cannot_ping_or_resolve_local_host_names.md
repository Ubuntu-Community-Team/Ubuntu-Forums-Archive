---
title: "Cannot ping or resolve local host names"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by stephenplank on 2009-01-03
I've relatively new to linux, so be patient with me.

My system can't resolve local host names, of which are mostly windows machines.  If I ping from terminal I get "unknown host"

However, using "net lookup" - it resolves perfectly?  Strange?

Any idea what the problem is?

Thanks 
Stephen Plank
New Zealand

---

### Post by meddle on 2009-09-17
1) Make sure your /etc/resolv.conf contains directions to a nameserver :
e.g. : [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-07/msg01664.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2007-07/msg01664.html)
2) Make sure you have dns listed before NOT FOUND in /etc/nsswitch.conf 
i.e. : hosts:          files mdns4_minimal dns [NOTFOUND=return] mdns4
via : [https://answers.launchpad.net/ubuntu/+question/58386](https://answers.launchpad.net/ubuntu/+question/58386)

Regards

---

