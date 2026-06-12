---
title: "Upcoming recordings vanish when I add tuner to slave backend"
date: 2013-04-20
forum: Mythbuntu
---

### Post by joelsplace on 2013-04-20
First off this isn't mythbuntu it's LINHES 7.4 with MythTV 2.5.3-23 but the guys over at the mythtv-users IRC said I should ask here because there are some really smart myth guys here.
I have a master/slave backend setup.  It has been working fine with 6 PVR150s.  3 in the master, 3 in the slave.  Charter decided to kill analog signals which made my PVRs worthless.  I bought 2 Ceton InfiniTV 4 PCIe cards and installed one in my master and one in the slave.
When the one is installed in the master everything works like it should.  As soon as I configure the tuners in my slave the upcoming recordings go blank.  I can watch live TV and record with "R" and get all 8 tuners recording fine.  I just can't schedule recordings and my previously scheduled upcoming recordings are gone.  I get this error [http://pastebin.com/WisXj1QP](http://pastebin.com/WisXj1QP)
If I remove the tuner config from the slave and reboot the master the upcoming recordings come back and the error goes away.  I've tried "delete all tuners" and deleting my Schedules Direct data source with "delete all" and then re-add everything several times but it still does exactly the same thing.  I also tried the optimize db script.
Help! Thanks,
Joel

---

### Post by jlp_engineer on 2013-04-24
I had a similar problem when I was configuring my first master/slave backend configuration.  I too tried LinHES, but was more comfortable running Mythbuntu.  You should give it a try.

What I did was to add the tuner in the slave first, then add the tuner in the master backend.  Strange as it sounds, that worked for me.

---

### Post by joelsplace on 2013-04-24
I tried that also.  The slave tuner works until I add the master tuner.  I wonder if LinHES does anything funny with the db or if I can use it as is in MythBuntu?  I've got years of use in it that I would rather not lose.
Thanks!

---

### Post by jlp_engineer on 2013-04-24
I would create backup images for bare metal recovery on both your backends (use something like CloneZilla), and then load the latest version of Mythbuntu and see what happens.  I have had a lot of little things that were bugs in one distribution and not present in the other distro, using the same version of MythTV.

It might be worth a shot...

---

### Post by joelsplace on 2013-04-24
I've been hoping to avoid that but it may be my best option if I can't find someone that can help me figure out what is going on with my current setup.  Thanks,  Joel

---

### Post by PhilWig on 2013-04-25
There's lots about configuring slaves here:
[http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26](http://www.mythtv.org/wiki/MythTV-HOWTO_-_0.26)
Phil

---

### Post by joelsplace on 2013-04-25
That's a great resource but it's just got the basic slave stuff.  The slave was working fine with my old tuners.  I have some more info now.  Today I tried adding the second tuner to my master and it won't work with both tuners either.  One shows "has an error" and the upcoming recordings go away.  Either tuner alone works fine.

---

