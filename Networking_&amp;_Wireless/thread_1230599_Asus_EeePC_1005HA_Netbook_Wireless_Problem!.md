---
title: "Asus EeePC 1005HA Netbook Wireless Problem!"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by careyrn on 2009-08-03
I cannot get the wireless to work with Ubuntu on my new netbook.  I've searched and tried countless suggestions and I can't manage to get anything.  

I'm brand new to using Ubuntu so I need very specific instructions, if any smarties know what to do I would be forever in your debt.  I'll be checking this periodically for any questions you have that would help you... help me :).  Thanks!

---

### Post by careyrn on 2009-08-03
bump :) come on I could really use some help...

[http://ubuntuforums.org/showthread.php?t=1219931&highlight=unclaimed](http://ubuntuforums.org/showthread.php?t=1219931&highlight=unclaimed)

tried to do that but A) AR813X-linux-v1.0.0.9.tar.gz I can't find that driver on the website and
B) when I try to use that code on a similar driver it gives me

tar: AR18Family-linux-v1.0.0.10.tar.gz: Cannot open: No such file or directory

Even though its right on my desktop...

---

### Post by spd106 on 2009-08-03
You have th right file, it's just been updated to a newer release.

The terminal defaults to your home directory. The desktop is a separate sub-directory of this, so you'll need to "cd Desktop" first. Take care withe capital letters, Ubuntu's file system (EXT3) is case sensitive.

Use the "ls" command to see if the file is in the current directory.

---

### Post by careyrn on 2009-08-04
so if the file is on my directory what is the exact line of code i should type in terminal... and i can only do 1 line at a time correct?

---

### Post by careyrn on 2009-08-04
sudo insmod atl1e.ko

got there and it didnt work...

i changed the atl1e.ko filename in terminal to the one i thought it would be from my version atl1e.7 but no luck... said it wasnt found

---

