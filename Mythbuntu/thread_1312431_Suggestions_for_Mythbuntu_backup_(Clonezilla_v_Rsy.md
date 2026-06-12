---
title: "Suggestions for Mythbuntu backup (Clonezilla v Rsync)"
date: 2009-11-03
forum: Mythbuntu
---

### Post by Zeedok on 2009-11-03
I have a Mythbuntu system (still running 9.04) and I want to back it up, in case I stuff things up when upgrading.  I have my 1 TB disc partitioned with a 300gb ext4 partition and the rest as XFS.  I bought a new 1 TB USB drive for the backup.

I have tried clonezilla (standard live CD) without a lot of success - I have subsequently read that ext4 support is not enabled by default and that it is only possible to clone an ext4 partition with the alternate (I read jaunty, but there is now a karmic version as well) and some options in the "Advanced" or "Expert" mode.

I have also used Rsync (and Grsync) to backup my laptop and it works brilliantly.  If possible, I think I would prefer to use Rsync, rather than clonezilla, but I am worried that there may be problems rsyncing the "virtual" XFS partition . . . am I right, or will rsyncing "/" just work??

Grateful for any advice . . .

---

### Post by kja999 on 2009-11-03
I use and rsync of all my video/recordings/music, and then dump a complete copy of my database.
My reasoning being, for any DR scenario I will use the mythbuntu disc to get the box up, then just restore the files and database and i'm done.

---

### Post by Zeedok on 2009-11-03
> **kja999 said:**
> I use and rsync of all my video/recordings/music, and then dump a complete copy of my database.
My reasoning being, for any DR scenario I will use the mythbuntu disc to get the box up, then just restore the files and database and i'm done.

OK, seems like a good approach.  I want to make the process as simple as possible, that's why I wanted to just rsync the whole thing. Also, I want to backup the channel setup and guide setup - which is the most irritating to reinstall - as well as a bunch of other documents etc

---

### Post by kja999 on 2009-11-03
> **Zeedok said:**
> OK, seems like a good approach.  I want to make the process as simple as possible, that's why I wanted to just rsync the whole thing. Also, I want to backup the channel setup and guide setup - which is the most irritating to reinstall - as well as a bunch of other documents etc


I agree .. One thing I have found is that myth doesn't like finding capture card data in the system already. When I have done a restore I have found its added another two cards into the system for some reason.

---

### Post by Rhubarb on 2009-11-03
The clonezilla karmic cd worked fine for me when backing up a karmic install with an ext4 partition.
And yes, I've also imaged a karmic mythbuntu RC install fine without any problems (and restored it fine too).

Use whichever option you like, rsync and clonezilla both backup quite well.

---

### Post by Zeedok on 2009-11-03
> **Rhubarb said:**
> The clonezilla karmic cd worked fine for me when backing up a karmic install with an ext4 partition.
And yes, I've also imaged a karmic mythbuntu RC install fine without any problems (and restored it fine too).

Use whichever option you like, rsync and clonezilla both backup quite well.

So I could clone it with Clonezilla, then use Rsync for updates??

---

