---
title: "Strange secondary frontend connection problem after .28 update"
date: 2014-06-16
forum: Mythbuntu
---

### Post by rte24 on 2014-06-16
Hello, I am a long time mythtv user (well, around 5 years if you consider that long) and I've have a strange connection problem after upgrading to mythtv .28 from .25.  I decided to update because of the new python3 movie scraper at imdb as I couldn't stand not having metadata for a couple new movies in my library.  Everything seemed to go fine on my master/frontend combo machine, and my standalone frontend in my basement man cave, but I get weird permission errors on the basement machine.  I can play recorded tv on it fine, but anytime I try to watch live tv or a movie from my movie library I get a "could not connect to master backend, is it running" message.  The backend is 100% working and I can browse my library on the problematic frontend (without metadata) so I know it's partially connected, but can't play from my library or view any live tv.  This happens everytime, so I figured it's a permission error of some sort.  I tried to give the backend open access and apply permissions to all groups, but it still won't work.  I was just watching recordings for a coupe months and dual booting into Windows 7 whenever I wanted to watch live tv, but that's starting to annoy me and I'd like to get it fixed.  Thanks to all in advance, this is my first time actually posting in the forums, but I've found answers here many times.  I'll probably need instructions if you guys need any log files.

---

### Post by blm-ubunet on 2014-06-16
Need logs...
if you're using mythbuntu:
mythfrontend.real -v upnp,network > felog.txt

else
mythfrontend -v upnp,network > felog.txt

But how does win7 access liveTV? network tuner device?
MythTV expects exclusive access for scheduling.

Make sure your FE videos path (FE setup) does** not** intersect with BE video storage group.
Storage group videos can be accessed from any FE.

You're not using NFS/samba in parallel across myth boxes?

---

### Post by rte24 on 2014-06-16
Here's my felog.txt from the troublesome frontend (I had to delete the second half to fit it into the forums-hopefully there's enough info here to help).  I use an HDHomerun dual as my tv tuner for everything.  This computer dual boots mythbuntu front-end only and win7, but I've been doing that for long before this issue started.  I'll check my storage groups to make sure there aren't any problems there. As far as Samba/NFS sharing, they're both checked and installed from mythbuntu control center, but I've never set up any sharing with them.  There are two other windows 7 computers on my network, could they be causing problems?  Thanks.

[ATTACH]254004[/ATTACH]

---

### Post by blm-ubunet on 2014-06-17
Can you run with less verbose options then?
mythfrontend > felog2.txt

AFAIK MythTV requires exclusive access to tuners for scheduling to work. It does not expect/allow for a win box to be connected.

---

### Post by rte24 on 2014-06-18
[ATTACH]254035[/ATTACH]Here's the less verbose log.  Looks like it's saying the master backend ip is wrong, but I've checked it a dozen times and it's correct.  I've even got the backend set so it requests the same ip address every time at 192.168.2.4.  My Windows boot is hardly ever running, do you think it could have something to do with my problem?  Thank you for your help.

---

### Post by blm-ubunet on 2014-06-18
I would stop using IPv6.
[http://www.mythtv.org/wiki/Enable_IPv6](http://www.mythtv.org/wiki/Enable_IPv6)

There have been some recent IPv6 changes in master that could be the fix or the fault...I'm not sure what your real mythtv version is..

Should update your themes (FE setup)
Could get the RAOP key for Airplay if you have any iProducts.

---

