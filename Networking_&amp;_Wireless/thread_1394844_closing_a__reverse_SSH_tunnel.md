---
title: "closing a  reverse SSH tunnel"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2010-01-31
so i start it with 
ssh -f -R 4096:localhost:22  [email]me@server.com[/email]
and it comes up and someone can log in at the remote end. 

how do i close the tunnel from the initiating end ?
 netstat doesnt seem to identify my  end of the tunnel , unless im looking for the wrong thing!

---

### Post by Lars Noodén on 2010-01-31
> **pdc124 said:**
> so i start it with 
ssh -f -R 4096:localhost:22  [email]me@server.com[/email]
and it comes up and someone can log in at the remote end. 

how do i close the tunnel from the initiating end ?
 netstat doesnt seem to identify my  end of the tunnel , unless im looking for the wrong thing!

If you have only one tunnel from the initiating end, and that is the only instance of ssh running then something like this will work:

```

pkill -x ssh

```

Otherwise, another way is to find the process number with [ps](http://linux.die.net/man/1/ps) and then use [kill](http://linux.die.net/man/1/kill) on that process id.

```

$ ps u | grep ssh
 pdc124     *1680*  0.0  0.2  1076  3196 p2  S+    08:41AM    0:03.46 ssh -f -R 4096:localhost:22 me@server.com
$ kill *1680*

```

---

