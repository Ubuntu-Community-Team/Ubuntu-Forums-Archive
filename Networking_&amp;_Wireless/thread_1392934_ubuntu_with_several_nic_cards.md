---
title: "ubuntu with several nic cards"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by Mia_tech on 2010-01-28
guys, I have ubuntu and on top I installed vmware server. My box has several nic cards, but I find that when I'm doing something on the host that requires a connection either to the internet or the network, it takes for ever to make the connection, like if the box is trying to figure out which nic card to use; however, only one card is been used by the host the other ones are used by vm's, but regardless they are connected to the medium... 

any suggestions?

---

### Post by DGortze380 on 2010-01-28
> **Mia_tech said:**
> guys, I have ubuntu and on top I installed vmware server. My box has several nic cards, but I find that when I'm doing something on the host that requires a connection either to the internet or the network, it takes for ever to make the connection, like if the box is trying to figure out which nic card to use; however, only one card is been used by the host the other ones are used by vm's, but regardless they are connected to the medium... 

any suggestions?
 post the output of 

```

netstat -rn

```

---

