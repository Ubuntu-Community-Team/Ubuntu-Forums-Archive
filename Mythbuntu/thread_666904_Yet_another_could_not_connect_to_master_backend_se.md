---
title: "Yet another could not connect to master backend server"
date: 2008-01-13
forum: Mythbuntu
---

### Post by curtis1552 on 2008-01-13
I've checked several other similar threads, but they aren't helping.
I installed Mythbuntu with all the defaults, and enables all the extra packages in the Console. I've gotten video from VLC so I know that the card can work (PVR-150). 
I don't have a mysql.txt file.
I'm running this on one machine.

I'm fairly sure I'm a member of the MythTV group.
I could have an IP issue, but I can't seem to find where to check it.

Any help would be great, thanks.

EDIT:
IP set to 127.0.0.1, but might not be the same as the DHCP IP (where do you check this?)

---

### Post by curtis1552 on 2008-01-14
I fixed it! I fixed it!
After 3 days of adjusting and harassing my computer I ralized that my IP was set at 127.0.0.1 and it should have been 127.0.1.1!

---

### Post by larsolav on 2008-01-18
> **curtis1552 said:**
> I fixed it! I fixed it!
After 3 days of adjusting and harassing my computer I ralized that my IP was set at 127.0.0.1 and it should have been 127.0.1.1!

Why did this fix the problem? Isn't 127.0.0.1  the internal loopback for the machine? Did you have to change settings any where else in addition to the mythtvsetup -> General page?

I am having the same problem, I have tried using 127.0.0.1, 127.0.1.1, and the IP address given by the router. Still get that error message...

---

### Post by curtis1552 on 2008-01-18
open the network settings (right click network icon and select manual)

Click on the hosts tab and it will tell you your computer's IP address. You want the IP for the host name ** not localhost**. (this is no garuntee, just wah worked for me : host name can be found on the General tab)
I used that IP - which was 127.0.0.1 for my mythbuntu backend.
Make sure that your Master Server IP address is the same (you're installing both backend and frontend on one box, right?)

My wired connection is also set to roaming - otherwise my computer will not connect to the internet. (from connections tab)

---

