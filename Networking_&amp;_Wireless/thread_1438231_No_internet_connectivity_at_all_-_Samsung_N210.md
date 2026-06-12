---
title: "No internet connectivity at all - Samsung N210"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by Lil3 on 2010-03-24
Hello,

I just installed 9.10 on my Samsung N210 netbook yesterday. I was able to connect wirelessly to the internet both through my home WPA-encrypted wireless network, and at a public coffee-shop wireless network. Once I tried to use my home network again, however, *nothing* will connect. 

Wireless networks are still showing up in my network manager, but I cannot connect to my home network (the password is correct - I triple-checked). I also cannot connect using wired ethernet. Please help! This is driving me nuts!

I am a complete beginner so I appreciate any help you can give me.

---

### Post by Iowan on 2010-03-24
I hate when that happens, wish I had a fix for the wireless problem. One option might be to Edit Connections, and delete the other wireless connections (the coffee shop in particular). Probably won't help, but...
Check (post) **sudo lshw -C network** and **ifconfig -a** to see if the machine recognizes the wired interface (eth0?). It *should* be first choice if available. 
Having recently learned that (at least on 9.10) NM stores settings in */etc/NetworkManager/system-connections*, that's my new hammer - and all networking problems are nails... Still, you can view the interface files there to see if anything interesting pops up/out.

---

### Post by Lil3 on 2010-03-24
It does recognize eth0, so I'm not sure why I can't connect. I got so frustrated I'm just re-installing netbook remix. Thanks for the quick reply - we'll see what happens.

---

### Post by Iowan on 2010-03-24
Good luck - I'll be anxious to see if you get it fixed!

---

### Post by antrozous812 on 2010-04-19
The last post in 3weeks old, but I thought I would continue from this thread instead of creating a new one, as I think the problem still hasn't be solved. 
I was wondering if there's any chance that the upcoming Ubuntu version (out in 10days) will fix the problem...? 
I have just bought a n210 but have kept windows on it because of this problem. But I can't wait to put Ubuntu on it....

-C.

---

