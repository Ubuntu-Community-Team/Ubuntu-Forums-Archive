---
title: "Samba printing without logging in?"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by verbitan on 2010-05-21
Hi there,

Basically I have two printers shared on my Ubuntu server...one is a PDF printer which requires you to be logged in, as it will email you the PDF, fine, the second is a laser printer. Now, this works fine, if you are logged in...however, if you just turn on the computer and try and print, without having visited a network share already, then it will just queue the print, but never actually print it?

In my smb.conf I have set it to use a no password account 'nobody' on bad user, so that the public shares are accessible to anyone on the network. That works fine. However, even though i have added the nobody account to the printer admins, it will not print!

Any ideas?

Many thanks,

Nick

---

