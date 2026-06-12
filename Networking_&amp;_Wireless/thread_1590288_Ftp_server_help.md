---
title: "Ftp server help"
date: 2010-10-07
forum: Networking &amp; Wireless
---

### Post by joek71 on 2010-10-07
Hi guys

i setup FTP server, i can connect no problem but i cant see the files i put in there from FTP client ( FileZilla )
when i go in to that file via terminal i see the files but when i use ftp client i dont see the files, and i gave that directory chmod 777

Please help

thank you

---

### Post by luvshines on 2010-10-07
Is this issue only with Filezilla or even through the browsers ??

---

### Post by joek71 on 2010-10-07
I dont know how to test using browser.

this is what i need;
I have userX, i made him directroy /home/userX
now i need to give him ftp access to a file in that directory so he can change files and see the results in the browser.  he is a php programer.

---

### Post by SeijiSensei on 2010-10-07
Post deleted.

Mods -- Where's the normal vBulletin option to delete a posting?  Did you disable it?

---

### Post by luvshines on 2010-10-08
For checking through the browser, open any browser - mozilla,chrome etc and type:
ftp://<address-of-server>

This should ask for username/passwd and then display your files in the share

---

