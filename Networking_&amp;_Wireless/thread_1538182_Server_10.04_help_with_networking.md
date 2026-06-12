---
title: "Server 10.04 help with networking"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by hotpuppy on 2010-07-24
Okay, I broke cardinal rule #1 in computers, "don't screw with what works"
 
However, I'm using this as a learning opportunity before I reinstall the machine.
 
I have a server running Ubuntu 10.04 on a Intel Motherboard (desktop).
 
Changed the motherboard so I could facilitate a smaller case.
 
Lost my networking.
 
New mobo has a RTL 8168b/8111 in it.  I've read through the thread about this.
 
What I'm confused at is that if I load the "rescue install" I can get the network card working....
 
but when I boot back up the card no longer works.
 
How do I figure out why it works under the rescue install and propogate those changes to my install?
 
thanks,

---

### Post by jpl888 on 2010-07-24
The reason your networking has stopped is because the network card has changed. 

Ubuntu and other udev based distros store the network card to interface name relationship persistently so your machine has assigned eth1 to the new card and is subsequently not loading any config because you don't have a config specified in /etc/network/interfaces.

Simply ```
nano /etc/udev/rules.d/70-persistent-net.rules
```

Move the cursor down to line 6 and press "esc" and then "t". This will remove the persistent relationship. Reboot the server and your networking will magically work again.

You can thank me at your leisure ;)

---

### Post by hotpuppy on 2010-07-26
> **jpl888 said:**
> The reason your networking has stopped is because the network card has changed. 
 
Ubuntu and other udev based distros store the network card to interface name relationship persistently so your machine has assigned eth1 to the new card and is subsequently not loading any config because you don't have a config specified in /etc/network/interfaces.
 
Simply ```
nano /etc/udev/rules.d/70-persistent-net.rules
```
 
Move the cursor down to line 6 and press "esc" and then "t". This will remove the persistent relationship. Reboot the server and your networking will magically work again.
 
You can thank me at your leisure ;)
 
I appreciate the information... this is the explanation I was looking for.  I resolved the issue via another fix.  I swore I posted my fix but it isn't there anymore....

---

