---
title: "Dell Dimension 8200 network problem"
date: 2005-02-07
forum: Networking &amp; Wireless
---

### Post by tnilsson on 2005-02-07
I have two computers that run Ubuntu without any problems, but my third box
is a Dell Dimension 8200 with some sort of 3com 3c59x compatible network card.
Ubuntu insist to load the tulip kernel module instead of the 3c59x module for the network card.
I get a slow network connection due to this porblem. Adn a lot of dropped packets.


How do I tell the kernel to load the module 3c59x instead of the tulip module?

I also tried the Live CD for the "Sun Java Desktop", which loaded the 3c59x module 
for the netowrk card without any problems.

Best Regards,
Tomas
 :?:

---

### Post by mendicant on 2005-02-07
You can insert the module in /etc/modules, and/or make sure it makes no references to the tulip module.

---

### Post by tnilsson on 2005-02-08
Thank you for the reply.
Later last night I found out that it was possible to use the blacklist file for hotplug.
I added a row in the end of the file /etc/hotplug/blacklist containing tulip.
After a reboot everything was  working perfect!

The hotplug system was  a black hole for me.

 :smile:

---

### Post by tnilsson on 2007-04-08
I found out that I do not get an ip address after rebot.
My only solution is to run /etc/init.d/networking restart after reboot.
My network card if working out of the box with Mandriva 2007, but I have always had
som kind of probems with the network card on this Dell Dimension 8200.

Any clues?

---

