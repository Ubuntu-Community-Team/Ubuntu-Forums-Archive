---
title: "Please help! Network runs at 5 KB/s!"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by alex004 on 2009-02-06
I need the help of some more experienced Linux guys than me!
My network runs at only 5 KB/s. which I cannot understand.
:(
I want to find out WHAT makes my Ubuntu 8.10 think that 5 KB/s is a good download rate.
I assume this is a ping-pong effect between Linux and the router.
Using the same machine under Windows I got at least a 1 MB/s download rate.
All the typical tests I have made did not discover anything useful.
I would be very glad if anybody could give me some hints!
Alex

I put some output in the attachment ...

---

### Post by superprash2003 on 2009-02-06
please post output of ifconfig from the terminal

---

### Post by alex004 on 2009-02-08
This is my ifconfig, but I cannot find anything wrong in it ...

---

### Post by Osamabingandhi on 2009-02-08
have you logged onto your router and checked around? Otherwise ubuntu doesn't restrict network speed, never heard about it. Have you looked into the firewall in ubuntu, but it should not do anything with the speed. Install network tools or network manager. Not sure what i have installed it's in swedish. But i would look into the router mainly. I log onto by typing 192.168.0.1 in firefox....

---

### Post by alex004 on 2009-02-10
Thanks for the hints. I suspect the router, too.
Under Windows laptop/router works ok.
What I found out with Ubuntu:
Networkmonitor tells me a download rate of about 5 KB/s (downloading Ubuntu updates).
Same with evolution: very, very slow.
But, to make things even more confused, parallel I can download other things and the accumulated download rate increases to 30 KB/s.
Now I try to check this MTU/MRU/CLAMP-MSS thing ...

---

