---
title: "Reomve virbr0"
date: 2011-08-01
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2011-08-01
Hi all,

i have a ubuntu 11.04 64-bit server and i have installed some VM-server "stuff" i thought i had removed the packages as i dont want it no more !

how do i remove interface virbr0 ?

thanks

---

### Post by jmoorse on 2011-08-01
Hi, you should be able remove it with the command that follows.  Please make sure you don't have anything else that needs it

```

sudo brctl delbr virbr0

```

---

