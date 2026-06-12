---
title: "emails saved where on hdd in ubuntu 9.04 Evolution 2.26.1 email app"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by lse123 on 2010-02-17
emails saved where on hdd in ubuntu 9.04 Evolution 2.26.1 email app ?
how I make backup prior upgrade whole 9.04 ubuntu? is recommended, isn't it?

---

### Post by SoftPops on 2010-02-17
E-mail folders should in a hidden folder ".evolution/mail/local" which can be found in your home folder.
 
When I last upgraded/reinstalled I also ran "backup settings" from the "File" menu in Evolution and saved the file into my home folder.
 
I saved everything I needed into my home folder and then simply copied this onto a USB stick. I then did the same for my son's data.
 
Hope this helps.

---

### Post by lse123 on 2010-02-17
what file.ext is the emails in ?

Exist built-in backup capability in ubuntu 9.04? 

are you recommend use it or use copy/paste to my ext hdd ?

---

### Post by SoftPops on 2010-02-19
I have just re-checked and have found that running "backup settings" from the "File" menu in Evolution will actually save the entire ".evolution" folder to a file called "evolution-backup.tar.gz". This backup therefore contains all the Evolution settings and mail folders. The "evolution-backup.tar.gz" can be saved directly onto the ext hdd.
 
If necessary the "restore settings" option from the Evolution "File" menu can then be used to put everything back after the upgrade/reinstall.
 
Hope this clarifies.

---

