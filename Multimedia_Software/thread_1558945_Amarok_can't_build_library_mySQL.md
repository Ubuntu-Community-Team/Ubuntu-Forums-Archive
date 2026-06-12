---
title: "Amarok can't build library mySQL"
date: 2010-08-22
forum: Multimedia Software
---

### Post by jlab on 2010-08-22
First of all I just want to say I recently installed Ubuntu so I am very new at this whole thing. My problem is that Amarok will take a while and scan to build my collection but nothing ever shows up. Music used to not even play but after installing something it worked. I found on some different forums to run Amarok in debug and I found a line saying mySQL wasn't initialized. But I don't know where to go from here.

Also Amarok never closes. I always have to go to the system monitor and force close it (yes I know it pops up in the top tray, but selecting close from that drop down menu does nothing)

My music is on a "storage" partition I created that is shared between windows 7 and ubuntu. I can play files fine and create playlists but I cant get my collection to build.

Any ideas?

-Jlab

---

### Post by jlab on 2010-08-26
Anybody? I Honestly have no clue what I'm doing wrong

---

### Post by pescadorsp on 2010-09-15
I have exactly same problem here, no clue how to solve.

---

### Post by jlab on 2010-09-22
Okay so I fixed it, but I forgot exactly how, but I'll try my best. I think all I did was go to the software center and install every possible mySQL that looked good then made sure I selected search by tags in Amarok and it worked!

If you need to know more I can tell you what packages and what settings I have selected in Amarok

---

### Post by joe_newbie on 2010-11-22
I found that in my case amarok was not passing the password to mysql.

I have to edit the file /home/joe/.kde/share/config/amarokrc

and at the bottom added the Password=password line like so:

[MySQL]
CheckCount=1
Host=192.168.1.100
UseServer=true
User=amarok
Password=password

I found this fix here: [http://forum.kde.org/viewtopic.php?f=115&t=89052](http://forum.kde.org/viewtopic.php?f=115&t=89052)

In reference to these error messages:


amarok:    [ERROR!] Tried to perform escape() on uninitialized MySQL                                                                                                                    
amarok:    [ERROR!] Tried to perform insert on uninitialized MySQL

---

