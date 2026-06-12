---
title: "Banshee iPod Problems"
date: 2010-05-05
forum: Multimedia Software
---

### Post by TheStreetSpirit on 2010-05-05
Hello. I have been trying to get full functionality from the ipod syncing features of banshee. I have tried every means to get it to work completely. The problem that arises is that banshee copies all songs to the ipod seemingly get transferred. But upon unhooking the iPod it says "no Music". all the songs are filed as other. I am at a loss for ways to fix it. Any information you need I can provide. Thank you!!!!!!!

---

### Post by TheStreetSpirit on 2010-05-05
*updated to add*
same thing in rhythmbox. The files are all on my hard-drive and play perfectly on any music player. But they do not want to be compatible with my iPod. all are in .mp3 format

Specs:
120gb ipod classic
ubuntu 10.04
banshee 1.6.0
IBM thinkpad T60
~13,000 song music library

any help would be greatly greatly appreciated!!!

---

### Post by TheStreetSpirit on 2010-05-05
.

---

### Post by TheStreetSpirit on 2010-05-05
.

---

### Post by Johnny B on 2010-05-05
i have never used banshee, and im sorry i can't help with that. I suggest, if you have no other options, try using gtkpod to transfer files (package: gtkpod or gtkpod-aac for included video support)

---

### Post by lisati on 2010-05-06
Threads merged.

---

### Post by TheStreetSpirit on 2010-05-07
I am at the end of my rope with this...[IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/mad.gif[/IMG] I had assumed after  plentiful research that this was a permissions issue and ubuntu wasn't  giving me the authority to write to the iPod. So I ran banshee in sudo  and synced one album. Then I unmounted it like the previous poster  suggested and then ejected. It worked!!!! So I sudoed banshee again and  tried to sync my entire library. Woke up this morning and got the same  result as all the last times. No music, all songs are categorized as  "other". Any more suggestions before I put my head through a wall? [IMG]http://c0491962.cdn.cloudfiles.rackspacecloud.com/images/questions/images/smilies/headscratch1.gif[/IMG]

---

### Post by islandis on 2010-05-07
I used to have this problem back when the iPod Classics first came out, and the Linux support was a bit sketchier.  Getting your music actually seen by the iPod involved a one time set-up like the one described [here]("http://www.kennedyprojects.com/kp1/?p=191").

You might try having a look at your SysInfo file and making sure that FirewireGuid line is in there.  If not, get it in there manually.

---

