---
title: "UFW: How to disable limit / burst limit rules?"
date: 2012-10-23
forum: Networking &amp; Wireless
---

### Post by Londo on 2012-10-23
Hello, 

I don't have much experience with the UFW, so this is probably a stupid question, but I'll ask it anyway. 

Having setup UFW quite painlessly I noticed some unexpected entries in /var/log/ufw.log - namely some connections were blocked that shouldn't have been blocked. After a quick investigation I noticed that iptables -L displayed quite a few more rules than I had set up with UFW - I guess these are UFW defaults. 

The one rule causing problems was:

```
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK] '
```

However I was unable to find any reference to this rule in any of the files in /etc/ufw/ or anywhere else for that matter. The rule is quite unnecessary, though, and I'm worried that it might cause some unexpected issues. 

So, how do I prevent UFW from performing rate limiting completely?

Thanks.

---

