---
title: "how to turn off afs3-callback service?"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by cowboyspike on 2011-01-20
I want to start weblogic application server on port 7001, but port scan list on localhost shows a afs3-callback service occupying the port.
 
*port     state    service*
7001    open    afs3-callback
 
The problem appeared after I upgraded from ubuntu 9.x to 10.04 (LTS *Lucid Lynx*) yesterday (I was running welogic on 7001 without any port conflict on 9.x).
 
I want to know how I turn off* afs3-callback* (or the parent process that started it) and if that will resolve the issue.
 
thanks.

---

