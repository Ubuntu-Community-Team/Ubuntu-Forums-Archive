---
title: "SSH Permit-Specified-User without-password option?"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by Ubu_Guy90 on 2013-08-20
Hi,

I'm looking to setup my SSH server to allow my primary user to login using key-auth only, but allow other users password authentication.  I'm thinking of something similar to "PermitRootLogin without-password", is there anything like this for other users? If not, how might I go about this?

Thanks

---

### Post by CharlesA on 2013-08-20
Check out the Match directive.
[http://www.manpagez.com/man/5/sshd_config/](http://www.manpagez.com/man/5/sshd_config/)

---

