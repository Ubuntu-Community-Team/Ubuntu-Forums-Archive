---
title: "Computers connected to network"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by white_shadow on 2009-12-12
Hi

How could i see wich computers are connected to my network?

Thank's in advance

---

### Post by Mski35 on 2009-12-12
You can view computers on a network using gnome by going to Places, Network.  From kde open  Dolphin then click on Network in the left hand pane, then click on Network.

---

### Post by lisati on 2009-12-12
One of my routers has an option to let me show a list of attached devices.

---

### Post by 5BallJuggler on 2009-12-12
> **white_shadow said:**
> Hi

How could i see wich computers are connected to my network?

Thank's in advance

Type this into a terminal.

sudo nmap 192.168.1.* | grep "192.168"

assuming your network is 192.168.1.1

Hope this helps
Phil

---

