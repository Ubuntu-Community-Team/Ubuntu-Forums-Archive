---
title: "Moving the mythtv mysql db to a Synology DS207+?"
date: 2010-04-30
forum: Mythbuntu
---

### Post by rgbiernat on 2010-04-30
Hi there,

I am running a mythtv backend on an AMD Athlon 2 XP 4800+. It has 2 * DVB-S2 Hauppage cards in it. I am using powertop to find "wakeup reasons". I see that my system gets woken up quite often because of mysql reads and writes. Now coming to my final question:

Would it make sense to move the mythtv database and the storage pool to my Synology DS207+ which runs 24/7? That way (off course with more tweaking) I could put my local disks to sleep.

What do you recommend? 
Move the DB with phpmyadmin? 
Or better set up the DB from scratch - with all the hassles of finding and modifying the 1000+ channels? :-)

Cheers,
rgbiernat

---

### Post by ian dobson on 2010-04-30
Hi,

If you really want to run the database on your NAS then just export the DB using phpmyadmin or mysqldump then import it into your other box.

I'm not sure what the performance of your NAS is, would it be enough for mysql?

Once that's working you just need to change your mysql.txt file to point to the IP address of the NAS and change the login name/password.

Regards
Ian Dobson

---

