---
title: "help with wireless!"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by isaiah83 on 2010-02-27
I'm having trouble getting my wireless card to work. I downloaded drivers on hp but it didnt seem to work. Can anybody help me?

---

### Post by thomas144 on 2010-02-27
I'm new to Ubuntu, and given your problem, you probably are, too. I might be able to help. Go to applications, then accessories, then Terminal. Type in
```
lspci
```
and you can highlight and copy the output of the command. If you put it on a reply to this post, someone else might be able to help you, or even I could. Please also post the output of
```
 
rfkill list

```
The first command should reveal what wireless card you have, and rfkill list tells if your wireless card is powered off or not.

---

