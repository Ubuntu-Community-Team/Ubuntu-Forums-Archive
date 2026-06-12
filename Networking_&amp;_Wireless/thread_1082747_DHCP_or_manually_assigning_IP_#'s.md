---
title: "DHCP or manually assigning IP #'s"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by MartyBuntu on 2009-02-28
What are the advantages of one over the other, having Ip #'s set automatically or manually at the router?

---

### Post by Iowan on 2009-02-28
DHCP (automatic IP's) are generally easy.  My laptop doesn't care whether I'm at home or at work - it asks for an IP, gets one, and works merrily away. With a manual IP, I'd need to change it whenever I went somewhere else.  
On the other hand, my servers work better if they have the same address - it's harder to hit a moving target.  My current DHCP server doesn't tie hostnames to IP addresses, so I must either remember the IP address (I wrote it on the front of each machine) or include it in the **hosts** file. I had it in the **hosts** file of my dial-up router (which was my local DNS server) until I recently upgraded to DSL.  DNSMASQ reportedly links (local) DNS with DHCP, but I haven't tried it.

---

### Post by pparks1 on 2009-02-28
DHCP is great when you have many computers on your network.  It's just an ease of administrative thing mainly.   If you only have a couple of computers, it's often just as easy to manually set the IP address on the computer.

---

