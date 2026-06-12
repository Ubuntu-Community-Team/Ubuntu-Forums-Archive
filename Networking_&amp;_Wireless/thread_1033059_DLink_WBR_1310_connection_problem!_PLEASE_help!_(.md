---
title: "DLink WBR 1310 connection problem! PLEASE help! :("
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by memod on 2009-01-07
Hello fellow Ubunters (Idk) lol so I got problems with my WBR 1310. See, I got two desktop computers, one downstairs (Mine) and the other upstairs (my mom's), and my computer is the one that has the internet access (we got internet thru the cable company, so the modem we use its by my computer). So that's the reason I got this wireless router, so that from this computer, I can give internet to my mom's computer.

So recently I was having problems with my internet connection, I used to have Windows Vista, and the internet would drop all of a sudden randomly. And I got curious with Ubuntu, tried the Live CD, the internet actually worked! So I decided to install Ubuntu instead! Now, before this, while I was still using Vista, on one of my desperate actions trying to connect online, I tried to reset my router, after that, that's when I got tired and switched to Ubuntu.

Now my problem is, the router got reseted, so now it doesn't have the key to get the online connection (WEP I think its called). My mom needs it because she can get on it normally, but she doesn't have to type a key in, that's the problem, anybody can get on it and use the internet for free, and I don't want that! So I tried to go to the set up page on 192.168.0.1 and whenever I try to access that site, I get kicked off the internet and my connection falls again, and it reconnects itself after a few seconds. But literally, I can't access that set up page! I tried doing some stuff I searched and found on the forum but none of them worked for me. What am I doing wrong? I'm still pretty new at Ubuntu, only a few days old. So I am not too advanced and don't know too much about it. Thanks for your help!

---

### Post by memod on 2009-01-07
Anyone? I'm really tired of my internet going slow, I think its people trying to steal my internet lol

---

### Post by memod on 2009-01-07
Sorry to spam, but I really need to stop the person that's using my wireless internet lol I can't even disable the wireless because I have to do that from the configuration page and I can't even access it :(

---

### Post by memod on 2009-01-07
Well, apparently I solved this problem now!  All I did was go to terminal and type network-admin
after that, I unlock the menu and I go to wired networks and enable dhcp! Apparently that was my problem the whole time ago. Thanks anyway!

---

