---
title: "Cannot connect to internet using pppoe"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by emiliano67 on 2009-07-30
Hi,
I have installed Ubuntu 8.04 alongside Windows XP sp3. I cannot connect to the internet. I have a broadband pppoe connection, ethernet.
The modem is Corega.
I did the sudo pppoeconf and it asks for a password but I don't have any. I connect with root and no password. And anyway if I try to write something when it asks for a password I cannot, it doesn't write.
Apparently, from the number of posts on the same issue, there are quite a few people that have difficulties with connecting to the internet. 
Any help would be appreciated, thanks.
Emiliano

---

### Post by laloruelas on 2009-07-30
you should talk to your isp and ask for the pppoe username and password.

---

### Post by emiliano67 on 2009-08-01
Got the datas I need but when I run sudo pppoeconf it says that I have to become root before running it!
What do I have to do?
Thanks
Emil

---

### Post by emiliano67 on 2009-08-01
Ok, privileges were already set but I re-set them and now it works (?!?).
Scanned the Ethernet interface and said:

Sorry, I scanned 2 interfaces, but the Access            &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.

My connection works fine when I'm using the windows OS...I'm posting right now through it.
Thanks
Emil

---

### Post by emiliano67 on 2009-08-01
Well, now it works. It said again that the the "Access Concentrator of your provider did not respond" but it connected. I'm posting using Firefox running on Ubuntu. Problem solved, somehow..

---

