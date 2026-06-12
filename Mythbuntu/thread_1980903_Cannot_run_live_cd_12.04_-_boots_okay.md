---
title: "Cannot run live cd 12.04 - boots okay"
date: 2012-05-16
forum: Mythbuntu
---

### Post by Ozdemon on 2012-05-16
I am running Linux Mint 11 atm. I have installed Myth 0.24 fixes as a combined BE/FE. It works with no problems.

However I would like to try Mythbuntu 12.04, but I cannot work out how to set it up as as test system. On bootup I have the choice of  a permanent install of Mythbuntu (I am not ready for that yet) or test a frontend if I have a network Backend. But I don't have a network B-E.

So my question is whether it is possible to test MB 12.04 in my situation?

---

### Post by josephmills on 2012-05-16
Have you tried it in virtual box or qemu or anything like that too get a feel for it ?

---

### Post by Ozdemon on 2012-05-16
I didn't think to try it in VBox. I will give that a shot, thanks.

---

### Post by 2F4U on 2012-05-16
When I ran MythBuntu 12.04 the last time, the default option was as a combined front- and backend, so that everything was combined on one machine.

---

### Post by nickrout on 2012-05-16
> **2F4U said:**
> When I ran MythBuntu 12.04 the last time, the default option was as a combined front- and backend, so that everything was combined on one machine.

Not in the livecd there isn't. But there are options to change that when you install, you choose what role you want your computer to play.

---

### Post by superm1 on 2012-05-16
If you don't want to wipe your box, it is possible to actually run the backend off the live CD, but you will need to manually do a few things:

1) Mount a hard disk or large USB disk.
2) Copy the contents of /var/lib into that disk.
3) Unmount the disk.
4) Remount the disk at /var/lib.  Basically it will be the backing for that directory now.
5) Re-enable the upstart jobs for mythtv-backend and mysql by renaming the jobs in /etc/init
6) Start mysql
7) Run mythtv-setup
8) Start mythtv-backend

I haven't tried all of that myself, so no guarantees it will actually work.  It's not something we've tested.

Another (far easier) route is to replace your HDD in the box temporarily and install to that replacement HDD

---

### Post by thatguruguy on 2012-05-16
> **superm1 said:**
> 
Another (far easier) route is to replace your HDD in the box temporarily and install to that replacement HDD

Couldn't you also install to an external HD, and then boot off the external HD?  That's how I typically test alpha and beta builds of Ubuntu, for example.

---

### Post by nickrout on 2012-05-17
> **thatguruguy said:**
> Couldn't you also install to an external HD, and then boot off the external HD?  That's how I typically test alpha and beta builds of Ubuntu, for example.

Yes, in fact I am posting this from mythbuntu 12.04 installed on a 8G USB flashdrive. A bit slow, and I can't record big files, but it is useful to prove it works.

---

