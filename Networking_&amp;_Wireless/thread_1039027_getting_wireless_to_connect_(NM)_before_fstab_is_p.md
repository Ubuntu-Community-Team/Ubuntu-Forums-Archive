---
title: "getting wireless to connect (NM) before fstab is processed?"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by finite9 on 2009-01-14
Is this even posible?

Using Ubuntu 8.10 on a laptop with ipw3945 and NetworkManager.

I have NFS shares on a server and enter them into fstab, but my wireless is not coming up until after I login, and then fstab is alerady processed.  I sa there was a "system setting" in nm-applet and assumed this was meant to enable the connection before login, but it did not work and after rebooting, the check box was empty again.

Is thee any way to do this without having to use a shell script on my desktop to mount the NFS shares?

---

