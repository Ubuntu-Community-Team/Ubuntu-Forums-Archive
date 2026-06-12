---
title: "Upgraded to 12.04 and can no longer browse samba shares without a password"
date: 2012-05-05
forum: Networking &amp; Wireless
---

### Post by KeithLM on 2012-05-05
I had this working just fine in 11.10.  I have several public shares on my Ubuntu system, and then I also share home directories.  Simple, straightforward use case, I've been doing this for a decade.  But every time I update the OS or samba makes a change this seems broken.  

The issue this time is that when I'm in Windows and attempt to browse the server, I am prompted for a username/password.  This is not the desired behavior.  I shouldn't be prompted for that until I try to open a home directory.  Once I provide the username/password I entered in smbpasswd I can browse the public shares, but when I try to browse the home directory it prompts for a password again and it is rejected, some dialog about multiple connections from one computer not allowed.  

Is the nobody account disabled in Ubuntu 12.04 by default for some reason?  If so, how do I enable this?  Why is there such a change from one version of Ubuntu to another?

---

### Post by KeithLM on 2012-05-05
Well now I got public shares, but no home shares.  Wonderful.

---

