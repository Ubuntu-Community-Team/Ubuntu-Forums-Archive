---
title: "Bridge a wired/wireless connection"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by nightspades on 2009-12-30
I have a dell inspiron 1525 I have wanted to use linux for some time now, i spent the whole day yesterday and after 5 hours i finally got the wireless to work! It was difficult but i'm happy that it works, anyway. The only thing holding me back from switching to 9.10 as my sole OS as opposed to win. 7, is the fact that i can no longer bridge a connection.

I have a 360, and can not afford to waste money on a wireless adapter, i use my laptop to bridge a connection from the 360 to my wireless card. In windows it was easy, but i have not come across an easy way to do it in ubuntu 9.10 yet, karmic is cool, but this would make it the best, so thanks ahead of time. And for the record.

Woot, first post :D

---

### Post by foxy123 on 2009-12-30
> **nightspades said:**
> I have a dell inspiron 1525 I have wanted to use linux for some time now, i spent the whole day yesterday and after 5 hours i finally got the wireless to work! It was difficult but i'm happy that it works, anyway. The only thing holding me back from switching to 9.10 as my sole OS as opposed to win. 7, is the fact that i can no longer bridge a connection.

I have a 360, and can not afford to waste money on a wireless adapter, i use my laptop to bridge a connection from the 360 to my wireless card. In windows it was easy, but i have not come across an easy way to do it in ubuntu 9.10 yet, karmic is cool, but this would make it the best, so thanks ahead of time. And for the record.

Woot, first post :D
You may try the following. Go to Edit Connections in NetworkManager, in Wired add a new connection. Go to a IPv4 Settings tab and choose method Shared to other computers. Then connect your 360 to your laptop over Ethernet and see if it picks up the connection.

---

### Post by skunkanova on 2009-12-30
in situations like hooking a piece of equipment to another typically requires a crossover cable as well as setting to share does it not?

---

### Post by Liam Mitchell on 2010-01-03
Thats awesome, worked first time. Wish I'd found it earlier, even signed up to these forums to say thanks!

---

### Post by jeraldjunkmail on 2011-01-30
ubuntu 10.10 Wired and wireless wired/wireless wireless/wired wireless and wired bridge

There.  That should help the next guy google it!  Thanks for posting this, as I am behind a NAT and wanted to forward my traffic from my Ubuntu server to my desktop...

As an aside, it is now showing my wired connections as 10.x.x.x addresses, I'll have to play with that perhaps for my purposes, but sytill very happy.  Thanks!

---

