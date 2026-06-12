---
title: "UFW Default Role"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by mastermindg on 2009-06-27
Does UFW Block ALL incoming traffic by default? If so, DENY rules would be used strictly when you are adding networks and want to add exceptions? I'm curious about this because I'd like to only allow port 80 and port 22 traffic externally and all others should be blocked.

---

### Post by 3rdalbum on 2009-06-28
By default, UFW does not block anything. The default Ubuntu install does not contain any outward-listening services.

I believe you'd do this:

```
sudo ufw default reject
```

says "Reject everything except where there is a rule"

```
sudo ufw allow 80
sudo ufw allow 22
```

After taking my advice, check your configuration with the Shields Up! website.

---

