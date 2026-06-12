---
title: "Migrating from Knoppmyth to Mythbuntu"
date: 2010-11-20
forum: Mythbuntu
---

### Post by marc.aronson on 2010-11-20
I have been running Knoppmyth for many years and I am going to try migrating to Mythbuntu. I am running Knoppmyth R5.5 (mythtv 0.22). Can someone give me a rough outline of what I need to do to preserve my current database & recording?. I am comfortable with Linux...

Thanks!

Marc

---

### Post by iponeverything on 2010-11-20
> **marc.aronson said:**
> I have been running Knoppmyth for many years and I am going to try migrating to Mythbuntu. I am running Knoppmyth R5.5 (mythtv 0.22). Can someone give me a rough outline of what I need to do to preserve my current database & recording?. I am comfortable with Linux...

Thanks!

Marc

I would work from a copy of you disk as it will give you an easy to revert. 

You will have to selectively restore the tables related to your recordings -- the tables structures will not match up, so you have to fair amount of tweaking to get to this to happen. 

I tried this about 6 months ago, but reverted back because it too much of a pain and my wife is very impatient when it comes to her mythtv. Much to my surprise, my serial ir blaster was mucked in the new release also..

Document your experiences and post back, as I am going revisit this again and would be great help.

---

### Post by alien878 on 2010-11-20
I did that last May.  Basically, what I did was:

[LIST=1]
[*]Take a clonezilla image of the root partition.  You are trading one set of quirks for another set of quirks, so you may want to go back.
[*]Install Mythbuntu on the old root partition.  Mount /myth as before when it asks you about the mounts.
[*]Fix up all the directories for video, gallery, tv, etc. in the setup.
[/LIST]This doesn't recover your recordings in the database.  I wasn't worried about them, so I just deleted them.  If you really want them you can probably google to find out what tables need to be restored, but it probably won't be easy.  You could also try doing a full restore of the DB, but that will probably cause some problems too.

Oh, yeah.  LIRC is a bit of a mess in 10.11 at the moment for some remotes.  You might want to search the forums to see if whatever you are using works.

---

### Post by marc.aronson on 2010-11-20
Thanks for the feedback. I'm already planning to use one of my spare disk drives so that I can revert. My myth box is a back-end only system so I'm not worried about LIRC support working well.

It seems like the key issue is the database version. How does this sound as a strategy:

[LIST=1]
[*]Update my Knoppmyth system to the latest version (LINHES). This way I am on the same version of mythtv that mythbuntu uses.
[*]Backup the database
[*]Restore the table "recorded"
[/LIST]

There are a few reason I am interested in mythbuntu:
[LIST=1]
[*]I would like to be on a standard distribution rather than a special mix. This way I can leverage the knowledge I build about the knits-and-knats of who Ubuntu has set things up on other Ubuntu machines.
[*]I recently acquired an iPad and an iPhone. I want to do transcoding to h.264 and my sense is that there has been quite a bit of progress on the codecs and encoders since R5.5 was created. ie, Faster, better, etc.
[/LIST]

I'd be interested in any feedback people might have on this thinking...

Marc

---

### Post by alien878 on 2010-11-21
One thing to watch out for if you restore individual tables is that you will have to fix up any references it may contain.  For example, I believe table Recorded references table Channels which may change on a new install.  There may be other tweaks needed.

You might have more luck if you try MythArchive to backup/restore the recordings.  I haven't tried it, but I think it has a native backup option that should do it.

Update:  I see someone seems to have figured out what tables need to be migrated here:  [http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

I don't know what version of myth that worked with though....

---

### Post by marc.aronson on 2010-11-21
> **alien878 said:**
> You might have more luck if you try MythArchive to backup/restore the recordings.  I haven't tried it, but I think it has a native backup option that should do it.

Update:  I see someone seems to have figured out what tables need to be migrated here:  [http://www.mythpvr.com/mythtv/tips/migrate-recordings.html](http://www.mythpvr.com/mythtv/tips/migrate-recordings.html)

I don't know what version of myth that worked with though....

Good ideas -- I'll check into them. I've got all my tuners working. Now I am struggling getting mythexport working. Once that is confirmed working, I'll migrate.

I've noticed that the front end is very unstable -- the front end will simply die when I attempt to play some of the recordings. Since I am not using the front end for anything but configuration it doesn't matter, but it is unfortunate...

Marc

---

### Post by nickrout on 2010-11-21
You should NOT do a partial restore of the database. Restore it all. Believe me!.

Use these utilities:

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

So - 

[LIST=1]
[*]backup the database.
[*]take a copy of all your data OR preserve the partitions they are on when you install mythbuntu
[*]drop the database mythbuntu created
[*]restore database
[*]set locations of files in myth-setup (storage groups section)
[/LIST]

---

### Post by nickrout on 2010-11-21
Oh and I have always regretted going from knoppmyth to mythbuntu, and make go back as part of my move to 0.24.

---

### Post by marc.aronson on 2010-11-22
> **nickrout said:**
> Oh and I have always regretted going from knoppmyth to mythbuntu, and make go back as part of my move to 0.24.

I'd be interested in hearing more of your thoughts and experiences on this. I am facing an upgrade either way as I am currently on KM R5.5. The migration to LINHES changes things around quite a bit, so it's the logical time to re-think my platform. Thanks!

Marc

---

### Post by nickrout on 2010-11-22
> **marc.aronson said:**
> I'd be interested in hearing more of your thoughts and experiences on this. I am facing an upgrade either way as I am currently on KM R5.5. The migration to LINHES changes things around quite a bit, so it's the logical time to re-think my platform. Thanks!

Marc

I made the change around April 2008 (IIRC). At that time I really wanted multirec so was keen to upgrade to 0.21. knoppmyth was lagging on getting 0.21 ready to go so I took the plunge and moved to mythbuntu.

I found it lacked the polish of knoppmyth. Some stuff just didn't work right and it took me a week or so to get the system how I wanted it. There were stupid errors which made it clear stuff just hadn't been tested. But I stuck with it and am stil using it.

LinHES looks promising, but the relative inaction on the forums means one of three things:

1. not many are using it; or
2. not many are supporting it; or
3. it doesn't go wrong much so no one bothers to post.

---

### Post by alien878 on 2010-11-22
I moved to mythbuntu because I wanted the flexibility of a full distribution.  LinHES is very limited in the packages available.  However, that is probably one of the reasons Knoppmyth/LinHES is much, much more stable then mythbuntu.  It has a group of testers that concentrate on the small set of packages provided.  They also don't release until they are happy with the stability, so they aren't bleeding edge.

With mythbuntu, I've learned to *always* take a clonezilla of the root partition before upgrading even a small set of packages.  In 6 months, I have been hit with showstoppers 3 times forcing me to restore and wait until the problem is fixed.

That said, my system is very stable right now.  Probably as good as LinHES was.  I just have to watch upgrading packages (distro upgrades are even worse. 10.4 was completely unusable for me. 10.11 was okay once I figured out the LIRC quirks).

---

### Post by marc.aronson on 2010-11-22
Very interesting feedback. I current use KM R5.5 and it is very stable. I only use it as a back end -- my front end is XBMC as I have implemented a [low power architecture ]("http://mythtv.mlaronson.com/low-power-mythtv-architecture")using a combination of XBMC, mythtv and a DLINK NAS. The only reason I am thinking of upgrading is to get the latest ffmpeg and H.264 codecs for transcoding. 

I wonder if I would be better off continuing to use my stable r5.5 system for my backend, and using a virtual machine running on top of R5.5 with a very current distribution for transcoding...

Marc

---

### Post by alien878 on 2010-11-22
I don't mean to scare you off.  It depends a lot on the HW.  I would recommend cloning your root dir and giving it a go.  It only takes a few minutes to restore the root dir if you don't like it.

I was lucky and found a stable state.  I just have to be careful to only permanently upgrade to other stable states.

---

