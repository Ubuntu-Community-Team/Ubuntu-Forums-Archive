---
title: "Ubuntu samba share shows full path instead of name of file/directory"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by quini on 2013-04-30
Hi!

After uprading from 12.04 to 13.04 Amd64 I've found a problem related to my samba share:

Wrong behaviour (test from 4.1 & 4.2 android machines) is:
-share called "Compartit" is shown as "/Compartit",
-directory called "Utils" within "Compartit" share is shown as "/Compartit/Utils" (should be shown as "Utils"),
-file called "Photo01.jpg" in directory "Utils" is shown as "/Compartit/Utils/Photo01.jpg" (instead of only "Photo01.jpg"), and so on.

That makes the name of the file/directory to hide because it's too long.

I was using a public, non writable user share; I've tryed removing it and adding a share in smb.conf with same result.

Any idea?  TIA  ;)

---

