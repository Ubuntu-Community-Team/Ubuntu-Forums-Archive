---
title: "can't connect to 1 website ¦ ping &amp; tracert work though"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by plasmafusion on 2009-07-13
hi all.
got a rather frustrating problem with accessing my blog [http://cloudplasma.co.uk](http://cloudplasma.co.uk)
i recently changed my hosting and moved it a cloud based host (the servers are based in a rackspace data center).
i can't access the blog from my home adsl line. i can access every other site i've tried fine though.
i can ping it and tracert works no problem so it doesn't seem like a dns issue. i can access it through a proxy. tried firefox, opera 10, links, chrome...none work. the page just stays 'waiting'. no error messages are displayed. the visit shows up on the blog's logs too. it can be accessed from everywhere else i've tried (6 ips).
the worst of it all is that i can access it using vista and firefox (which i kept on my laptop after i bought it but shrunk its partition down to 30gb) through the same router.
i can see no reason why windows would be able to access it but ubuntu cannot (also tried mint & fedora using live cds).
someone please help!!

---

### Post by quixote on 2009-07-15
I had a weird probem like this once with all typepad blogs.  Everything else was accessible, but no typepad blogs, and there's a lot of them.  It was the damndest thing.  I tried everything, but what helped was rebooting my router.  I have no idea why that helped (nor did a networking expert whom I asked) but I thought I'd share it in case it helps you.

---

### Post by plasmafusion on 2009-07-15
hi quixote and thanks for your reply.
i've rebooted the router repeatedly acquiring various new ip addresses in the process but still can't connect with any linux distro. 
the webhost says nothing is blocking on their end and the isp (talktalk broadband uk) say the same (although their tech support leaves something to be desired).
i've resorted to running tor and privoxy whenever i need to access the blog from home but this method slows things to a crawl.
i'd love to get to the root of this matter. can anyone else shed some light on the problem?

---

### Post by plasmafusion on 2009-07-15
well after much more head scratching i've found the answer.
i changed the mtu value for eth0 from 'automatic' to 1432 (the value the router was set to).
i've never encountered an error like this using any os but i'm just glad to have it sorted.
if this helps anyone and prevents as much frustration as i've endured then colour me glad.

---

