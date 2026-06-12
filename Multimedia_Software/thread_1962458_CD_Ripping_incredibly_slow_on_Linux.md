---
title: "CD Ripping incredibly slow on Linux"
date: 2012-04-21
forum: Multimedia Software
---

### Post by BigSilly on 2012-04-21
OK, I'm using Precise at the moment, and obviously it isn't actually released yet, but I've had this problem on my last Linux install that I replaced with Precise, so it's not an Ubuntu-only problem.

It doesn't matter what program I use for ripping my CDs, it takes forever on Linux. I've tried all sorts, from Asunder to Banshee to Sound Juicer, and they're all slow. Pop the same disc into my W7 install using the same settings on Windows Media Player (ripping to 256 kbs) and it flies. If I let the Linux program finish and listen to the tracks, they're very poor quality and skip all the time. It's a similar story if I try to rip my DVD's using Handbrake, though I haven't tried it yet with Precise since it's not out yet for it.

Why is Linux suddenly having these issues with my DVD drive? It's a Pioneer DVR-216D. I checked the firmware and it's the last one they released for it.

Halp!

---

### Post by BigSilly on 2012-04-21
Found this command on Google - hdparm -I /dev/cdrom - and I get:

```
bigsilly@bigsilly:~$ hdparm -I /dev/cdrom

/dev/cdrom:
 HDIO_DRIVE_CMD(identify) failed: Bad address
```

Is this relevant? It's the same result if I enter /dev/dvd. Thanks all.

---

### Post by hakermania on 2012-04-21
I can't really help much, but I've ripped many many CDs with my laptop and I didn't have this issue. I was using a program whose name isn't in my mind right now :P

EDIT: it was one of the common programs of USC, so I don't think you haven't already given it a try...

---

### Post by BigSilly on 2012-04-21
> **hakermania said:**
> I can't really help much, but I've ripped many many CDs with my laptop and I didn't have this issue. I was using a program whose name isn't in my mind right now :P

EDIT: it was one of the common programs of USC, so I don't think you haven't already given it a try...

I've never had the problem before in all the years of using Linux! But it's very odd as it was exactly the same on my openSUSE install that I was using up until this week when I installed Precise daily over it. At the time I just presumed that I'd messed up the openSUSE install somehow and it was time to move on. I didn't anticipate that the issue would follow me to Ubuntu.

I'm currently trying Sound Juicer again, but it's reporting the drive is extracting at 3.6x speed, and will take 12 minutes to rip. :(

If anyone has any ideas please let me know. :)

---

### Post by hakermania on 2012-04-21
Have you *lately* tried with windows' programs? Maybe your drive has been damaged or something (meanwhile)?

---

### Post by BigSilly on 2012-04-21
> **hakermania said:**
> Have you *lately* tried with windows' programs? Maybe your drive has been damaged or something (meanwhile)?

Yes I tried it this morning.

---

### Post by hakermania on 2012-04-21
> **BigSilly said:**
> Yes I tried it this morning.

Well, then the fact that altogether the programs in linux stopped working as expected means that they all share something (a library, a command etc) in common, that changed in a way that doesn't co-operate well with you drive.

That's what I can think of :/

---

### Post by BigSilly on 2012-04-21
> **hakermania said:**
> Well, then the fact that altogether the programs in linux stopped working as expected means that they all share something (a library, a command etc) in common, that changed in a way that doesn't co-operate well with you drive.

That's what I can think of :/

Yep, that's pretty much what I'm thinking too. It must be something very recent that's seen an update.

---

### Post by BigSilly on 2012-04-21
This is odd. Trying a few other discs now and they seem to be ripping fine. Very quick no problems. I wonder if I just have a couple of particularly troublesome CDs? They are all retail and original discs. I dunno, but I think possibly the drive, and Linux, are both fine.

Very confusing though. The troublesome discs in question rip fine in Windows. :confused:

---

### Post by Donny Bahama on 2012-07-30
I hope this thread isn't too old to revive.

I'm having the same problem as the OP. I'm ripping audiobooks on CD and I can't believe how long they're taking compared to my Windows rips. :(

Additional details: DVD-RW drive is an LG GSA-T20L in an HP laptop. While ripping, Banshee seems to average between 1.2X and 1.4X. Each track seems to start out at 12X, then gradually slows down to 1.2~1.4X.

---

