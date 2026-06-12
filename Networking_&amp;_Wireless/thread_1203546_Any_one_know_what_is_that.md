---
title: "Any one know what is that ?"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by gawadelnil2002 on 2009-07-03
hey guys i was trying to opne port on router for transmission torrent client and i succeded and and its very nice that i can download torrents with high speed , but just my mind scratched me to search for open ports for my ip using network tool and i found another 2 ports are open on my pc ,is all 4 prots open two for transimssion the web inetrface one and the the other prot is for the ordinary use of transimision from my desktop in addition for another two ports that i didnt open i didnt use i dont know how is that open why, is that by default or what i dont know , fastly i closed transmission and i scanned my ports again i found only two ports, and that made me sure that there is two ports are open with no need cause transmission dont use them,and the strange thing that every time i make scan the two ports appears open but with different numbers sometimes 58469 and 42157 , and sometimes another number but they still two , can any one tell what is that , and why its open , im going curious and i dont know if that safe or not

---

### Post by Boondoklife on 2009-07-03
post the output of
```
sudo netstat -an
```

---

### Post by gawadelnil2002 on 2009-07-04
> **Boondoklife said:**
> post the output of
```
sudo netstate -an
```
sorry i cant do this when i type that in terminal it says (netstate: command not found) so itdosnt work im waiting for u to tell me what is the right order

---

### Post by Boondoklife on 2009-07-04
Sorry I fat fingered an extra e, it is sudo netstat -an

---

