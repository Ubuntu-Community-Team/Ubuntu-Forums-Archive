---
title: "vlan &amp; ipup"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by Jova on 2006-02-25
I need to run 4 vlan-s on maj eth0. I just put in /etc/init.d/ifupdown at start section 
 /sbin/vconfig add eth0 2
...
 /sbin/vconfig add eth0 5

and in stop section

/sbin/vconfig rem eth0.2
...

and configure vlans in /etc/network/interfaces

I'm not shure that's right way. If some body know better way please tell me 

tnx

---

### Post by flickerfly on 2006-07-27
I'm trying to make this work. Any chance you could take a moment to provide a bit more detail on what exactly you did? I've managed to create the interfaces, but I can't seem to bring them up. It sounds like you have. Are you using the ifupdown-scripts-zg2 package? Thanks.

---

### Post by mips on 2006-07-31
Dunno if this is any help [http://www.ubuntuforums.org/showthread.php?t=187195&highlight=vlan](http://www.ubuntuforums.org/showthread.php?t=187195&highlight=vlan)

---

