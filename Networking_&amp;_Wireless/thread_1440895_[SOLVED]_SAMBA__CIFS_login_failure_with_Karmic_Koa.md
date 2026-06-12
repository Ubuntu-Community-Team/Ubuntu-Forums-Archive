---
title: "[SOLVED] SAMBA / CIFS login failure with Karmic Koala - punctuation in sudo password"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by Troilus on 2010-03-28
Someone might find this useful:

After upgrading my desktop computer (DESKTOP) and my eeepc laptop (LAPTOP) to Ubuntu 9.10, Karmic Koala, I found it impossible to access password-protected samba shares. 

More accurately, I could not access password-protected LAPTOP shares from DESKTOP, but it worked in the other direction.  I realised that the only thing that differed on the two computers was the sudo password.  The desktop password began with a punctuation mark - a bracket.  When I changed the password, the share finally worked.

It took me three weeks to figure that out, so if anyone else has the same problem, perhaps this post will help.

---

