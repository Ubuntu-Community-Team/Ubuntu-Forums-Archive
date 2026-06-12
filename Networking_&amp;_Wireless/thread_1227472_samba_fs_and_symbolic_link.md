---
title: "samba fs and symbolic link"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by caue.rego on 2009-07-30
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=123008&stc=1&d=1248991435[/IMG]

So, the image is pretty self-explanatory.

Anyone can tell me why that happens?

I'll explain it: there's a ubuntu configured with samba sharing any given folder. In it, there are 2 symbolic links for directories, one is pointing outside the shared one, the other one is an insider.

When I go through regular samba-nautilus integration, those sym links are transparent, everything is fine. Great!

But when I've configured smbfs on fstab and try to see the same share there, the links are broken! wtf?!

Any lights?

---

