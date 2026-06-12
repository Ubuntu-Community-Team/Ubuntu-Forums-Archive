---
title: "Viewing Windows share in Nautlius (Samba)...this might work"
date: 2005-03-07
forum: Networking &amp; Wireless
---

### Post by buldir on 2005-03-07
I have seen many people mentioning that they could not view Windows shares with Nautilus.  Try this at the command prompt:

$ nautilus smb://username@ip_address_of_windows_box/share_name

So, if you're username is monkey and the IP address of your Windows box is 123.456.789.1 and the shared folder name is bananas, it would be:

$ nautilus smb://monkey@123.456.789.1/bananas

Worked for me!

---

