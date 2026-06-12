---
title: "umask and Samba - Permissions question."
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-11-14
Currently I have directory mask + create mask settings in my smb.conf to force any files/folders that come across the network to my server automatically take on 775 permissions.

If I set the umask the the parent directory to 775 that people are saving their files to on my actual server, would that take away the need for me putting create mask 775 + directory mask 775 settings in my smb.conf?

---

