---
title: "Windows shares"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by zugu on 2006-07-11
Is there anything I need to do in order to access a Windows LAN I'm connected to after a fresh Daper install? Like installing Samba and configuring it?

I'm asking this because I can only see 10 computers in a 400 computers LAN. And they have nothing shared, or at least it seems so. 

Cheers.

---

### Post by Thund3rstruck on 2006-07-11
You need samba, but that's only if you want the client tools. You mount shares with smbfs or smbmount. You query machines with nmblookup. Take a look over the man pages. You can even add the machine to your windows domain which may give you better visibility throughout the rest of the domain

---

