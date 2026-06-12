---
title: "tunnels &amp; rdp"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by moty12 on 2011-04-17
Hello,
I want to login to my university server, in windows i used Putty and rdp.
the setting in putty (download to my ubuntu and runnig) SSH-> tunnels 
destination:  2.bgu.ac.il:3389 
source port:7000
on local
session SSH type 1.bgu.ac.il port:22

so far so good i logged in and i can see the files on the 1.bgu

the next step is to open RDP and ask him to login localhost:7000
Not Working, i use Gnome-RDP and Remmina Remote Desktop Client no luck on both. 
any ideas?

---

### Post by sefs on 2011-05-29
> **moty12 said:**
> Hello,
I want to login to my university server, in windows i used Putty and rdp.
the setting in putty (download to my ubuntu and runnig) SSH-> tunnels 
destination:  2.bgu.ac.il:3389 
source port:7000
on local
session SSH type 1.bgu.ac.il port:22

so far so good i logged in and i can see the files on the 1.bgu

the next step is to open RDP and ask him to login localhost:7000
Not Working, i use Gnome-RDP and Remmina Remote Desktop Client no luck on both. 
any ideas?

You did not say what errors you got.
Sometimes I find I have trouble without setting the tunnel (in putty) explicitly to ipv4 instead of leaving it at auto.

---

