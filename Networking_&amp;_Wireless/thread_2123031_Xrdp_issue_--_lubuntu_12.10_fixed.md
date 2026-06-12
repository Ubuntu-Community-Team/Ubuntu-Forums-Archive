---
title: "Xrdp issue -- lubuntu 12.10 fixed"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by joelseeley on 2013-03-06
this fix is for Lubuntu 12.10 xrdp
I was able to fix mine by doing the following from home directory:

the file i edited was located /home/jon/.xsession

i added:

startlubuntu

after this it worked!! and that was after several hours of trying to figure it out. so do the following at the prompt to fix:

"gedit .xsession"
add the line "startlubuntu"
save and exit
restart and it works.

---

