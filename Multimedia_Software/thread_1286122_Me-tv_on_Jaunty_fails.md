---
title: "Me-tv on Jaunty fails"
date: 2009-10-08
forum: Multimedia Software
---

### Post by momist on 2009-10-08
Hi everyone.

Since my upgrade from Intrepid to Jaunty, Me-tv has failed for me.  At first it went OK, with only the main four channels present, but after the re-tune required in September I've had nothing but trouble.

This is now a clean install of jaunty, but with a separate /home partition.  It seems that Me-tv is picking up it's channel configuration somewhere, but I can't find where.  The documentation says it should be in channels.conf, but file search doesn't find that anywhere in the file system.  I've tried complete removal of everything to do with Me-tv in synaptic, but when I re-install, it still picks up the faulty channels.

Can anyone reveal where this is now kept - it must be called something else in the jaunty version?

Thanks!

---

### Post by rogerp1 on 2009-10-08
Its in the .me-tv folder in your home folder.

Delete the database or the folder and it should recreate a new one when you re-scan

---

### Post by momist on 2009-10-08
> **rogerp1 said:**
> Its in the .me-tv folder in your home folder.

Delete the database or the folder and it should recreate a new one when you re-scan

Thanks for that rogerp.  The .me-tv folder being a "hidden" folder, the search function couldn't find it.  I think it a fault with the search function in Ubuntu that there is no option to also search hidden folders, or for hidden files, or at least not on the user interface.

I've now got it working OK - so thanks very much for the pointer.

---

### Post by rogerp1 on 2009-10-09
Good to hear you got it working.

Ive been trying to use it but couldnt get a good enough picture quality so Ive gone back to using Kaffiene

---

