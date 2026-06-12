---
title: "Disk burning in Natty"
date: 2011-01-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by lowbagger on 2011-01-22
Does anyone else notice that when burning a DVD from a .iso image the disk burning utility starts over again when it's finished?  I've ruined 2 DVDs because it finishes and then starts recording again on the same disk.  I'm using 11.04 Natty Narwhal (Satanic Edition :evil:).

---

### Post by ronacc on 2011-01-22
install k3b it works fine , cd-creator and brassero are for making coasters :lolflag:

---

### Post by Quackers on 2011-01-22
Are you using Brasero? I haven't found that problem.

---

### Post by VMC on 2011-01-23
> **ronacc said:**
> install k3b it works fine , cd-creator and brassero are for making coasters :lolflag:

I prefer k3b, but then you need to pull in all the KDE files with it-or a lot of them. I wish the creators of k3b would create a gnome version.

When I want serious burning I just fire up my Kubuntu and use k3b.

---

### Post by Mr. Picklesworth on 2011-01-23
> **ronacc said:**
> install k3b it works fine , cd-creator and brassero are for making coasters :lolflag:

That isn't exactly helpful. We're here to fix problems with Ubuntu's default experience ;)

---

### Post by Harry33 on 2011-01-23
There are a lot of recent bug reports on the issue.
I found these two new ones concerning Brasero and DVD's:

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/705750](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/705750)

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/702557](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/702557)

Both of those are for Maverick (10.10).

---

### Post by cariboo on 2011-01-23
It would really help if the op told what application he is using.

---

### Post by rbrick49 on 2011-01-23
i used brasero on natty to burn amd64 iso natty and brassero made some errors on the dvd it told me installer was corrupt so I downloaded k3b and did a reburn all was ok so I would suspect its a bug in brassero should have kept the log but forgot I had to use dvd as iso file was over size for cd
i am using dual core amd system on my box
by the way i was using natty i386 on my box when I downloaded and burnt the dvd if that is any help

---

### Post by MacUntu on 2011-01-23
> **Mr. Picklesworth said:**
> That isn't exactly helpful. We're here to fix problems with Ubuntu's default experience ;)

You can't say Brasero has no bugs reported, yet people complain every cycle about problems with simple tasks. Want a better user experience - replace Brasero.

---

### Post by ronacc on 2011-01-23
> **Mr. Picklesworth said:**
> That isn't exactly helpful. We're here to fix problems with Ubuntu's default experience ;)

I realize we are here to fix problems with Ubuntu and in fact give both cd-creator ( although that one has never worked for me ) and brassero a try  with each new dev cycle, but when I need to burn good cd/dvd's I grab K3B and actually brassero worked very well for me during Karmic  (or was it lucid)but not this time the same goes for usb-creator  I give it a couple of chances then go with unetbootin atleast I don't have to use the result of that effort as mini frizbies.

---

### Post by VMC on 2011-01-24
> **rbrick49 said:**
> ... installer was corrupt so I downloaded k3b and did a reburn all was ok so I would suspect its a bug in brassero should have kept the log but forgot I had to use dvd as iso file was over size for cd
...
You might check your home folder under "~/.config/brasero" for any references to log outputs.

---

### Post by w3rt on 2011-01-24
Brasero works fine for me, maybe use a dvd rw to save wasting dvds until the problem is solved

---

### Post by mc4man on 2011-01-24
While over the last several ubuntu releases brasero has worked ok here when testing it (80% or so success, prefer a prog w/ 99+% - Imgburn), the biggest issue is doesn't work most of the time or at all for a lot of users.
When it does fail it usually does so cryptically, forcing users to search out possible solutions (if any), or wait for a fix (if any

What's somewhat interesting is that a lot of users having issues w/ brasero get better results when switching genisoimage to mkisofs  and wodim to cdrecord, though I doubt ubuntu would ever consider doing so (debian will never do so

ppa that does the switch, works atm in natty and also provides cdda2wav that can be used instead of icedax  (app side adjustment for some apps

To switch search cdr in synaptic, mark cdrecord and mkisofs for install, genisoimage and wodim will be automatically removed and dependencies will be maintained
[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

Edit: if inclined to try/switch thru ppa you must edit the 2 source entries to show maverick in Distribution - screen

---

### Post by Gremlinzzz on 2011-01-24
I prefer gnomebaker.

---

