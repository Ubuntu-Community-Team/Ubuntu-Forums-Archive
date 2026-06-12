---
title: "creating a LAN network between 2 computers"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by levent20 on 2009-05-23
Halo,

Searched a bit over the internet to find a way to connect 2 computers with no success unfortunately. Can someone pls provide a how to or some advise as to how to create a LAN network between 2 computers.

Kind Regards,
Levent20

---

### Post by levent20 on 2009-05-23
sorry my desktop is using the 9.04 version of ubuntu.
Thanks

---

### Post by zobcat on 2009-05-23
You need to purchase (or look for a tutorial on how to make) a crossover cat5 cable. Once you have said cable, all you need to do is connect it to the ethernet ports of both computers and you have a 2 computer network.

---

### Post by Iowan on 2009-05-23
You can use a crossover cable, or insert a hub or switch between the two. Then, depending on what/how you want to share files, you will need to install the server-portion of a system - either Samba, NFS, FTP, or SSH. [here]("https://help.ubuntu.com/8.10/internet/C/networking-shares.html") is one help page.  [https://help.ubuntu.com](https://help.ubuntu.com) has more help pages on the other systems, too.

---

### Post by levent20 on 2009-05-23
by cat5 i suppose you mean an ethernet cable which i have. however how will i make the two computers look at each other?

---

### Post by ad_267 on 2009-05-23
> **levent20 said:**
> by cat5 i suppose you mean an ethernet cable which i have. however how will i make the two computers look at each other?

It has to be a crossover cable if you want to be able to plug each end of the same cable into each computer. Otherwise you need to use a switch/hub and use normal network cable.

If your computers access the internet using DSL and are both plugged into a router then this router should function as a switch and you should be able to set up a server application such as samba to share files, or install any other server application you'd like.

---

### Post by levent20 on 2009-05-23
Thanks guys for the replies will get on to it and let you know.
Kind regards

---

