---
title: "Automatic wired connection does not work..."
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by mendozaro on 2009-04-29
I installed Ubuntu 8.04 LTS on a new system and for the first time ever on a ubuntu comp, internet did not work. 

First i tried googling for known issues related to my network adapter but i could not find any. Next i copied the ip, dns... from windows xp (dual boot) and set my connection in ubuntu to manual and entered the info from xp. All worked fine on manual... until the ip changed from my ISP.

I also tried setting the connection to DHCP but no results. In windows my connection is set "automatically".

Is there any way i can make this work "automatically" in ubuntu on this machine to?? (all the other comps i ever installed ubuntu on worked from the start)

---

### Post by mendozaro on 2009-05-05
noone had this problem? no clues?

---

### Post by slakkie on 2009-05-05
Could you post your /etc/network/interfaces file here?

Are you using a network manager? If yes, which one, and could you post that configuration as well.

---

### Post by mendozaro on 2009-05-05
Am gonna do this latter when i get to the problematic computer.

Best regards.

---

### Post by Iowan on 2009-05-05
Results of **ifconfig -a** and **lshw -C network** might also be helpful.

---

### Post by mendozaro on 2009-05-08
So... after installing a router the computer mentioned in this post worked like a charm on roaming mode or auto DHCP.

Thank you all for your help!

---

