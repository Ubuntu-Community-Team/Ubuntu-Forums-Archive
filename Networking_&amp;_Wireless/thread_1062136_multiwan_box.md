---
title: "multiwan box"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by da mono on 2009-02-06
hi guys, I'm the new one :D.

well after searching and searching and come out as I started i mean almost in blank i decided to join the forum and ask :P, well here goes my main objective is to make my home server which has 3 NIC's to act as a multi wan router i have 2 2mbps/768kbps dsl lines, each one with a 2wire router modem (without wireless), the server runs as a nas, web server and F@H and i was thinking is the a way I can combine my to dsl lines into the server and use them as a huge data pipe my may concern is more the upload than the download geting my hands on a multi-wan router is a bit difficult at the time since I'm living in Mexico and those thing are extreme expensive to get, a 50dlls cheap one could end me costing around the equivalence of 250 dlls  

thx in advance for your responses :P


:popcorn:

---

### Post by wirelessmonkey on 2009-02-06
You'll need to look into interface bonding.  Someone not too long ago wrote a little explanation/howto, but I can't seem to locate it right now. 

Good luck.

---

### Post by da mono on 2009-02-06
well what i read form network bonding was that it was made for making backbones over servers but again i might be wrong since a haven't found a good explanation in network bonding

---

### Post by da mono on 2009-02-06
anyone else ???

---

### Post by wirelessmonkey on 2009-02-06
[http://ubuntuforums.org/showthread.php?t=1029811&highlight=bonding](http://ubuntuforums.org/showthread.php?t=1029811&highlight=bonding)

Whether or not it will work over interfaces from seperate providers, I don't know.


Make sure and read down a bit, adaptive load balancing seems like what you're wanting.

---

### Post by da mono on 2009-02-06
well actualy is the same isp so i hope it works thx for the thread

---

### Post by mushroom_mover on 2009-05-01
may i suggest you search on the term "broadband bonding" to see the various types of solutions are available out there for what you are trying to do. Best wishes...

---

