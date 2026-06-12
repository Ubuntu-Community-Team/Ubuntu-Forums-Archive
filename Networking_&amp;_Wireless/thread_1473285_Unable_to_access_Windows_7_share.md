---
title: "Unable to access Windows 7 share"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Nicolice on 2010-05-05
Hello, I'm currently using ubuntu on my laptop, and I want to access my windows 7 folders via network and file sharing...but there's this problem...

Everytime I want to connect to my Windows 7 pc, it will just prompt me a "password required for xx pc"...and keep looping on every username/password [afaik from the windows account], and I'm unable to login to it.

Even tho I've set "LmCompatibilityLevel" dword key, 1 or 2 [restarted every set] under LSA..it's still the same thing happens...

Any helps? Thanks

I'm using Windows 7 Home Premium

---

### Post by Nicolice on 2010-05-07
No one replied? :(

Anyway, found the problem for the looping password prompt...have to uninstall Windows Live Sign-in Assistant on Windows 7...took me hours to figure it out...

---

### Post by voltav on 2010-05-28
It works! Thanks :D

---

### Post by dafreak on 2010-06-03
Take comfort in knowing that it helped me solve my problem as well. Had the same issue and right after I removed the Windows Live Sign-in Assistant I was able to access my Windows 7 fileshares again. It must've been installed during an automatic Windows update because I don't remember installing it.

---

### Post by dullroar on 2010-10-30
Believe it or not, it worked for me, too, after MONTHS of frustration. Thanks for the post!

---

