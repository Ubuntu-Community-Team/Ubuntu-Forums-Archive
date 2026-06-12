---
title: "Nfs share dies on reboot"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Kilz on 2009-11-08
I am having a real fun problem and cant seem to solve it.
I have 2 linux computers 
1. A small server that has both Arch and Karmic installed. It has a linksys wireless card.
2 My main computer with Karmic installed hooked into the router by wire.

My router is a Linksys wrtgu54g

Regardless of what operating system is started on the server Karmic on main cant connect to the server to mount the shares. Even manually using sudo mount 192.168.1.102:/files /mnt/files fails. A ping to the server returns unreachable. Both computers have internet access. 

Here is where it gets strange. If I open a terminal on the server and ping the desktop. The shares mount on main and then I can ping the server.

I have blocked ivp6
The router lets me assign ips so they are static with dhcp.
No firewalls on any install

Is there any way to make this work automatically without having to ping from the server?

---

### Post by Kilz on 2009-11-09
Well it seems I have found the problem and I am going to post it here to help others. The problem is a setting on the router. Go to the Wireless tab, Advanced Wireless Settings subsection set CTS Protection Mode to auto. Save the setting and reboot the computers. I have rebooted about 10 times and nfs shares still show.

---

### Post by Bucky Ball on 2009-11-09
Thanks for sharing; might save someone hours ... ;-)

---

### Post by Kilz on 2009-11-09
No problem, the router is common, its distributed by t mobile. It only took 3 days of banging my head into a wall to figure it out. If it saves someone else the trouble the post is worth it. Im marking this one solved.

---

