---
title: "IPTables not saving drops"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Choragos on 2011-01-06
I have been using IP tables to block particular IP addresses, so I thought. Then I looked at what the rules are, and it's only saving my last entry (I think). I have been using this to block:

 ```

iptables -A INPUT -s xxx.xxx.xxx.xxx -j DROP 

```Upon running
 ```

iptables -L -n 
 
```at the end of the INPUT chain I see:
```

DROP       all  --  xxx.xxx.xxx.xxx       0.0.0.0/0 

```where the IP address is the last one I blocked. Am I doing something incorrectly? What's the difference between -A and -I? I read the manpage and didn't see what should have been a big difference. I specifically am blocking IP addresses that are attempting to ssh in, but I have no problem generally blocking them from any port.

Thanks so much.

---

