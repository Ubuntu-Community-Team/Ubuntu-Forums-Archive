---
title: "&quot;No Network Connection&quot; icon in panel but Wireless Works."
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Ziptar on 2006-06-03
My wireless card (Linksys WPC54G) works, I can surf the net (Making this post from my Laptop) and use Gaim but, the icon in panel shows the "No network Connection" Icon..
It's more of an annoyance really but, anyone know how to fix it?

---

### Post by sunexplodes on 2006-11-08
This exact thing is happening to me. Wireless is working perfectly, but I have a "No Network Connection" icon showing in my taskbar when I boot. 

I can remove the icon, but it reappears every time I log on. 

Any ways to remove this on a more permanent level?

---

### Post by skirkpatrick on 2006-11-08
Is it showing you a no connection for your NIC and not your wireless?  What notifier are you using?

---

### Post by sunexplodes on 2006-11-08
AH, never mind. Apparantly I had a "Network Manager Applet" installed that I didn't know about. It's gone now.

---

### Post by dynamicdude on 2007-03-23
any ideas friends as i m having the same problem... I have got no icon for wireless commection but an icon confirming "no network connection".

any help would be beneficial for me.

---

### Post by Jouke74 on 2007-03-23
Probably you configured your wireless connection through setup. Every connection that is in your etc/network/interfaces file will not be used by the gnome-network-manager. So it is either one or the other. 

You have two options, edit the interfaces file and remove all connections but the loopback. This way you will manage all connections with the net-work manager. Or the simplest is to remove the gnome-network-manager and the icon plus program behind it will be gone, the network management is done the way it's done now.

---

