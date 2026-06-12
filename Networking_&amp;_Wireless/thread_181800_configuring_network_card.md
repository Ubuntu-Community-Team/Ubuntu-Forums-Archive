---
title: "configuring network card"
date: 2006-05-24
forum: Networking &amp; Wireless
---

### Post by Strike&gt;&gt; on 2006-05-24
Hello

i have a very long ethernet cable running through the house, therefore i need to change the connection from 100mb connection to 10mb base connection. i can do that in windows, but i looked at the settings in ubuntu and the option wasn't there. is there any way that i can change it?

Thank you.

---

### Post by 0MG on 2006-05-24
Why do you need to change it exactly? If it isn't longer than 327 feet, you should have no problem. Even then, ethernet only works up to 327 feet. 
 
The interface should autosense by default.

If you need to change it, the syntax is:

sudo ifconfig *interface* media *type*

where interface would likely be eth0 and type would be 10baseT for 10Mb twisted pair

---

### Post by Strike&gt;&gt; on 2006-06-17
umm it didn't work:(

i got this error:

port: SIOCSIFMAP: Operation not supported 

windows xp can't auto sense it too, thats why i chnanged it to 10base. anything higher then 10mb full duplex won't work.

---

