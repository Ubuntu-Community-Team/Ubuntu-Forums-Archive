---
title: "Share Wifi Internet Connection To other Computer Through Cross over Cat 5 cable"
date: 2010-11-21
forum: Networking &amp; Wireless
---

### Post by The Creator on 2010-11-21
I will start with a big thank-you for reading my thread and trying to help!

I am having huge issues with trying to share my wifi connection to my other computer through a crossover cat 5 cable. 

Here is what I am trying to accomplish:

Internet ---->  Apple Airport Router ----> Wifi Radio ----> My Quad Core ---> Though Crossover Cat 5 Cable ----> My Pentium 4 Desktop

What I want is file sharing through samba between the two computers (I can do that once they can see eachother)

And for both of them to use my quad core's wifi internet. 

Currently I have firestarter with the dhcp3-server installed to try and do this but I am having no luck getting the two computers to talk. I can not use a switch between the two, I need to do this as a peer to peer network between the two computers. 

I am using ubuntu 10.10 on both computers (64 Bit) and need someone to walk me through it. I have tried many guides but to no avail.


Please Help!

Thanks!

---

### Post by spiky001 on 2010-11-21
If you right click network manager it will give you an option to edit then select wired open ivp4 then select shared with other pc

---

### Post by The Creator on 2010-11-21
Ok, I did it, but my pentium 4 still is not getting dhcp from my computer with the wireless. It is just failing to connect... 

Thanks!

---

### Post by spiky001 on 2010-11-21
I take it you done that on the 1 with wireless? Maybe restart eth0 net as well if you right click NM then untick enable network then retick it.  you said you have a firewall try it without any on the wireless pc

---

### Post by The Creator on 2010-11-21
Wow, you are a champ. the firewall is what did it. I read so many guides saying to use firestarter to bridge the connection but I guess it has been built into the distro recently. NO editing dns tables. thank you so much!



:KS:KS:KS:KS:KS


Yay!

---

