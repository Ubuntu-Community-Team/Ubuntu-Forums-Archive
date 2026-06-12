---
title: "Router configuration problem"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by Aleksej on 2011-12-03
Hi! Recently I changed my modem with a router, and now I don't know how to configure my network. I've searched the web, tried different solutions, but with no success. Before that, I configured the network with the command 'pppoeconf' and it worked. When i repeat that command now with the router, it says that it can't configure it because either there's a problem with cables or so, either there's something else controlling the pppoe or something like that.

Should I reset the network connection, and if I should, how do I do that? 

Thanks

---

### Post by bluexrider on 2011-12-03
> **Aleksej said:**
> Hi! Recently I changed my modem with a router, and now I don't know how to configure my network. I've searched the web, tried different solutions, but with no success. Before that, I configured the network with the command 'pppoeconf' and it worked. When i repeat that command now with the router, it says that it can't configure it because either there's a problem with cables or so, either there's something else controlling the pppoe or something like that.

Should I reset the network connection, and if I should, how do I do that? 

Thanks
its difficult to determine without additional information

what distro are you running
what kind of router
are you sure that the cables are connected properly

---

### Post by Aleksej on 2011-12-03
> **bluexrider said:**
> its difficult to determine without additional information

what distro are you running
what kind of router
are you sure that the cables are connected properly

Well, its Ubuntu 11.10, the router is Speedport W 503V, and the cables are working, coz now I'm using it, from the Windows partition (dual boot).

---

### Post by Aleksej on 2011-12-03
Well now, problem solved:) I searched through other threads here, and tried this:

> **praseodym said:**
> ```
gksu gedit /etc/network/interfaces
```remove anything _but_:
```
auto lo
iface lo inet loopback
```Remove your wired profile in "wired" and  "DSL" (if any) in the network-manager applet and reboot.
 
and it workded :guitar:

---

### Post by matt_symes on 2011-12-03
Hi

Log into the router using its IP address from a web browser and configure it that way.

What exactly are you trying to configure ?

**EDIT**: Glad you fixed it. 

You need to provide much more information about what the problem is in future though and you will get much better help. I, for one, thought you were having an issue with your router and not the configuration of your PC.

Kind regards

---

### Post by oldtimer7777 on 2011-12-03
And for future reference, most routers that are made today come with free tech support phone numbers for users to call, where they can walk you through the entire process getting them configured to work with your current Internet Service Provider.  All a user needs to do is go to the manufacturer's web site and look in support for a free phone number.  They can even test your connection as well to make sure everything is working ok.  A much more professional way of doing this kind of job too and will save you a considerable amount of frustration.

> **Aleksej said:**
> Hi! Recently I changed my modem with a router, and now I don't know how to configure my network. I've searched the web, tried different solutions, but with no success. Before that, I configured the network with the command 'pppoeconf' and it worked. When i repeat that command now with the router, it says that it can't configure it because either there's a problem with cables or so, either there's something else controlling the pppoe or something like that.

Should I reset the network connection, and if I should, how do I do that? 

Thanks

---

