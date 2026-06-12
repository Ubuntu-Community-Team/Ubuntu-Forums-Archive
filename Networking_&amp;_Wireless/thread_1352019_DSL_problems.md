---
title: "DSL problems"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by nishant.singh28 on 2009-12-11
I have problem connecting to my home internet connection in Karmic. It is a simple connection with a broadband modem, a username and a password. I had no problems connecting in Jaunty. I just selected a new connection under DSL and entered the username and password and Bingo but not in Karmic. Any suggestions?

---

### Post by gordintoronto on 2009-12-11
What do you mean by "under DSL"?  What result do you get?

---

### Post by Weird Kid on 2009-12-11
[SIZE=4][FONT=Times New Roman]My Ubuntu OS is 9.10 Karmic Koala.   I have no problem connecting to a high speed LAN internet connection, the network manager automatically detects and connects to a high speed LAN connection (wired).    My problem is that I can't get the network manager to detect or connect to a DSL internet connection (wired), I have tried running some command lines in the terminal in an attempt to manually configure and detect the connection but still no luck.   Does anybody no whats wrong? if so please help, any advice would be greatly appreciated.    [/FONT][/SIZE]

---

### Post by nishant.singh28 on 2009-12-12
Same here....I am using an old laptop running XP as the wireless router and accessing the network but can't connect directly. I have no idea as to what the error exactly is. Is there a way to diagnose the problem using command line?

---

### Post by anishd on 2009-12-18
Same problem with me.
I have understood that the network manager in ubuntu is defective in Karmic. You can only connect via terminal in ubuntu Karmic.
This is called regression.

---

### Post by anishd on 2009-12-18
visit here for a review on DSL on Karmic
[http://www.business-standard.com/india/news/ubuntu-910karmic-disconnection/376597/](http://www.business-standard.com/india/news/ubuntu-910karmic-disconnection/376597/)

---

### Post by editdigital on 2009-12-19
> **anishd said:**
> Same problem with me.
I have understood that the network manager in ubuntu is defective in Karmic. You can only connect via terminal in ubuntu Karmic.
This is called regression.



Hey there,
Same is the DSL dialup problem with me too. I used to have Jaunty and used to successfully initiate a DSL dialup from the Network manager after keying in the username and password simply. The internet used to worh just fine. Now, after installing 9.10 Karmic, the DSL dialup does not initiate a broadband connection. It connects to the iBall Baton router. I have used the same steps to configure the DSL here as I did in Jaunty.
I think something's wrong with the  DSL dialup in 9.10.
Please find a solution.

---

### Post by margemoosh on 2010-01-05
same problem!
i use terminal sudo pppoeconf and pon dsl-provider to connect.
but i couldn't use GUI to connect

---

