---
title: "Broadcom 802.11b/g WLAN not recognized by Ubuntu"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by Robohawk on 2010-05-03
Hey guys,
 
I have been trying to get on the Internet for a while on Ubuntu, but my wireless card wont work when I am using Ubuntu (I have Windows Vista installed also), the display stays red. All the technical talk in the other forums and tutorials is making my head spin because I dont know anything about what they are talking about so hopefullly there is a way to explain this without using a random string of letters and numbers to describe everything!
 
I am using: 
OS: Ubunto 9.1
Laptop: DV4T - 1000
Wireless card: Broadcom 802.11b/g WLAN
 
If you need any more specs I'll be happy to provide them but you may need to tell me how to find them 0.o
 
Thanks in advance!

---

### Post by TBABill on 2010-05-03
Are you close enough to plug into your router with an ethernet cord? If you are, plug in and update your system via System>Administration>Update Manager.

I have a Broadcom as well and anytime I install 9.10 or 10.04, I must first plug in and update to allow the system to enable the proprietary drivers. The update is not mandatory to do all this, but having all updates is a good idea. Mine is a BCM4312 and I use the B43 driver.

---

### Post by Robohawk on 2010-05-03
[LEFT]I did the update, but I still cant find my card.  I am using the ethernet connection now, but as soon as I unplug the wire I lose internet and cant get it back...
[/LEFT]

---

### Post by TBABill on 2010-05-04
After the update did you click System, then Administration, then Hardware? Did your system identify any proprietary hardware drivers available for your system after doing that?

---

### Post by Robohawk on 2010-05-04
No i did not, but I will now!

---

### Post by pdc on 2010-05-04
type in 

> lspci

and look to see what the broadcom details are .. ie is it 4312 or whatever ..

here is a guide to the broadcom drivers .. find the advice for your card ..

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

have a read; follow their advice

---

### Post by Robohawk on 2010-05-06
Alright, thanks a lot!

---

