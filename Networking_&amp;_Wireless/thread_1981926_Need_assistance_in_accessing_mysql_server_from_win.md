---
title: "Need assistance in accessing mysql server from windows7 laptop on same network"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by Headfirst on 2012-05-17
Greetings all,

First I'd like to thank you for taking the time to look at my issue. Now for my issue =)

I recently set up an old desktop to act as my home server. I put a fresh install of 12.04 on it and I've just finished configuring the rest of the LAMP packages.

While configuring mysql I modified the bind address in my.conf to be the IP address of my server which is 192.168.1.13 my understanding was that I needed to change this from the localhost IP address so I could access the server from other computers on the network. 

When I open firefox on the server itself and pull up localhost/phpmyadmin I get the expected phpmyadmin page. If I try to access it from my laptop that is on the same network by typing 192.168.1.13/phpmyadmin in firefox I get a message about the server timing out.

I'm hoping someone out there has a suggestion.. If I left out vital information needed to resolve this please let me know I'll produce said information ASAP.

Again, thank you fellow Ubuntu Forum members.

---

### Post by Headfirst on 2012-05-18
So I've done some of my own research and I thought perhaps it was because I didn't have Samba4 configured on the Ubuntu 12.04 machine. I went through that last night and that has not helped anything..

This stinks I thought it would be easier to access the phpmyadmin on that server since they are all on the same network! I must be missing something hopefully I can figure it out this has been a work in progress for 6months from building the server and now I'm reaching the final stages..

Any help would be much appreciated!

---

