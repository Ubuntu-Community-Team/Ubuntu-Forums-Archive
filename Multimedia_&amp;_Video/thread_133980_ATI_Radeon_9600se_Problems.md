---
title: "ATI Radeon 9600se Problems"
date: 2006-02-21
forum: Multimedia &amp; Video
---

### Post by DBAlex on 2006-02-21
Hi, Ive been using ubuntu for about 6 months now with no troubles, ive allways either searched this forum or found the way to do it myself however long it took me, now i have gone solo and im only running Ubuntu on my main PC, so last night i tried to install my graphics card driver to run some games more quickly but i couldn't get it working!

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.22.5-inst.html")

I followed these instructions from the ATI website and used "sh ati-driver-installer-8.22.5-i386.run" in the terminal and everything installed fine.

Then i got down to the point where im supposed to open the terminal and use "aticonfig --initial" this didnt work AT ALL! And I tried to get it working for 2 hours by changing directory to the folder or by editing the files (Dont worry i backed them up and restored them)

Heres a screenshot of the error message I get:
[IMG]http://img88.imageshack.us/img88/1660/aticonfig3vg.png[/IMG]


So im at my wits end now, i hope someone here can help me, its the first time  ive come unstuck in ubuntu!

I would post my xorg.conf, but i forgot where it is, its in /usr/... ?

Thanks if you can help anyway. :D

---

### Post by bjweeks on 2006-02-21
Don't use the drivers from ati use the ones in the repos.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver](http://help.ubuntu.com/starterguide/C/faqguide-all.html#installatidriver)

---

### Post by DBAlex on 2006-02-21
Thanks, Im installing them now!

Does it matter if i havent removed the other drivers? (I didnt know how to since i used a .sh)

Thanks anyway, Now I can do some fragging in Quake 3. :)

---

### Post by bjweeks on 2006-02-21
I'm not sure but it might just work:D .

---

### Post by DBAlex on 2006-02-21
Wohooo!

It works, Quake 3 is nice @ 800x600 but any res higher makes the mouse slow...

:(  I guess ATI drivers really arent that great in linux!

Oh well! I might be getting a new Nvidia card soon anyway...

---

### Post by bjweeks on 2006-02-21
Yep the ati drivers suck, nvidia suport is good but could be better.

---

