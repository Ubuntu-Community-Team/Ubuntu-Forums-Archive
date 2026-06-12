---
title: "Front End Live TV / Recordings Issue"
date: 2009-02-04
forum: Mythbuntu
---

### Post by lofttroy on 2009-02-04
I'm a newbie.  It's always a good place to start.

I've a backend up and running apparently fine.
(AMD Operton 1.9GHz Quad, 16GB RAM, 2TB Storage)

The front end starts up and runs okay.  I can watch live TV, browse the menus, etc, etc.

I set up two shows to record via mythweb and they recorded in /var/lib/mythtv/recordings like I would expect.  The live TV also stored where expected /var/lib/mythtv/LiveTV.

When I look for the recordings on the front end, I can see all of the worthless LiveTV listings shown in all their glory, but I can only see the recordings through the manage recordings menu.

I figure I'm doing something wrong with the storage groups, but I can't for the life of me see it.

Two requests:
1.  Can someone give me a link to the idiot's guide to storage groups? (The installation manual is a little light.)
2.  Any suggestions as to why my Live TV shows up under recordings and recordings no where.

Thanks,

Troy

---

### Post by newlinux on 2009-02-05
my first guess is that maybe you have a filter setup on your frontend to only show live TV.

Go to the watch recordings screens and hit "m" on your keyboard. Should show you what filter you are using and allow you to change it if it is not what you want.

---

### Post by newlinux on 2009-02-05
Oh, and with regards to #1:

[http://www.mythtv.org/wiki/User_Manual:MythTV_structure#Storage_Groups](http://www.mythtv.org/wiki/User_Manual:MythTV_structure#Storage_Groups)

---

