---
title: "PEAP/GTC RSA token retry &amp; lockout"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by the_original_billq on 2011-05-06
Our wifi uses PEAP authentication and GTC inner authentication.  The "password" is an RSA token with 60-second expiration.

NetworkManager tries to re-use the old "password" six times, resulting in a lock-out on our router.

Where/how can this be tuned, so it always prompts for a new "password" and will never re-try?

Thanks.

---

