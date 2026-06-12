---
title: "likewise-open and gdm login"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by zorro2b on 2010-12-16
I have finally managed to get likewise-open to work on my 10.04 desktop for active directory authentication. Now if I am logged on as a local user I can su to my active directory account, but if I try and login from the GDM I get an authentication failure.

auth.log says:
pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user

Do I need to make changes to pam configuration as well?

---

