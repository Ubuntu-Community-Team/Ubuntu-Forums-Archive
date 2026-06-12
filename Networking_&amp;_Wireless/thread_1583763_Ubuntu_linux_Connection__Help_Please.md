---
title: "Ubuntu linux Connection | Help Please"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by Kazavak on 2010-09-28
I read some threads in the "solved" subforum here and i managed to install my
Broadcom Corporation BCM4318 AirForce One 54 with ndiswrapped.
I can see two access points now,
they are called Zone 8 and Zone 9
so i connect to this Zone 9 for example but 
on the windows xp i used to connect via broadband connection 
that requires username and password this is the picture of it

[IMG]http://img844.imageshack.us/img844/9558/39988786.jpg[/IMG]

So how the hell do i connect to the internet with ubuntu?
Will it also require username&password or what?
Please help me as soon as possible :(

---

### Post by Kazavak on 2010-09-28
**OK!**I connected to internet with pppoeconfig and i have entered my username and pass and it worked,than i went to System>Administration>Hardware and i Enabled ATI driver,it downloaded and i needed 2 reboot,and now,when i rebooted i cant even see the wireless access points nor access to net and when i type pppoeconfig again into terminal it says 
that i must become root :S 

Tell me whats wrong

---

### Post by Iowan on 2010-09-28
> **Kazavak said:**
> ...and when i type pppoeconfig again into terminal it says that i must become root :S 

Tell me whats wrongTry it with **sudo**...

---

