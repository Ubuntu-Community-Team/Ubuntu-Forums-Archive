---
title: "Selected programs not connecting to the internet"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by pikeman47 on 2009-06-26
I recently set up a home network using a DLink dir-615 wireless router and for the first day or so, everything was working fine (my desktop connects to the internet via a wireless connection). Today, I turned on my computer and it connected to the internet fine and browsed as usual, however when i tried to open up pidgin or vuze, neither could connect to the internet. I believe it is an issue with only my computer. I tested to see if the other computers in the house (desktop running XP and a laptop running ubuntu) had the same issue but they worked fine and connected as they should. 
Any advice on how to get my programs to connected to the internet would be greatly appreciated. Thanks

---

### Post by superprash2003 on 2009-06-27
any specific firewall installed in that machine? like firestarter or ufw?

---

### Post by jhannah on 2009-06-28
I would also recommend you check System -> Preferences -> Network Proxy. You might have explicitly set Firefox to ignore system-wide proxy settings but, by default, most applications that are Gnome-friendly will try to make use of a proxy if it is configured in the aforementioned preferences section.

Beyond that, what happens if you try to ping something from a console window? Just to be on the safe side, you should check your IPtables rules as well:

```
iptables -nvL
```

That should report three empty IPtables chains but if it doesn't, your problem might lie there.

---

