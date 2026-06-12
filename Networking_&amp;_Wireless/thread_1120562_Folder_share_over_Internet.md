---
title: "Folder share over Internet"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by rdorin on 2009-04-09
Hello,

 I've managed to join my Ubuntu 8.10 server edition to the local domain (SBS2003) and share my folders over LAN with Samba. Domain users can access these folders over LAN, no problem (xp clients). My question is, what is the best way to share these folders over internet, so domain users can access them from anywhere ?

 OpenSSH is not a solution, managed to make it work but its not what im looking for.

 Any ideeas are welcome.

Sorry for my bad english :)

Thanks in advance.

---

### Post by inobe on 2009-04-09
ftp wouldn't be a bad start with security in mind.

---

### Post by superprash2003 on 2009-04-09
yea.. you could look at gproftpd.. you should also check out dropbox.. they have linux support.

---

