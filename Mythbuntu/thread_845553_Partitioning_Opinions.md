---
title: "Partitioning Opinions"
date: 2008-06-30
forum: Mythbuntu
---

### Post by rnelson0 on 2008-06-30
I'm sure this has been discussed in depth on the forum, but I'll ask anyway. My recent upgrade from Gutsy to Hardy on my Mythbuntu machine caused the machine to become inexplicably slow in some situations. So, I'm doing a fresh install... and I want to improve my partitions, so I want your opinions.

Right now, I have two 500 GB drives that are LVM'd into one drive. And I think I want to get away from LVM on this fresh install. On that drive I have a /boot, /swap, /, and /home (the LARGEST one). 
I'll also be buying a new 1 TB drive to add to the mix. Or maybe 500GB x2 instead of the 1TB?

So how would YOU divide 500GB (x2) & 1 TB for a new install?

---

### Post by tgm4883 on 2008-06-30
> **rnelson0 said:**
> I'm sure this has been discussed in depth on the forum, but I'll ask anyway. My recent upgrade from Gutsy to Hardy on my Mythbuntu machine caused the machine to become inexplicably slow in some situations. So, I'm doing a fresh install... and I want to improve my partitions, so I want your opinions.

Right now, I have two 500 GB drives that are LVM'd into one drive. And I think I want to get away from LVM on this fresh install. On that drive I have a /boot, /swap, /, and /home (the LARGEST one). 
I'll also be buying a new 1 TB drive to add to the mix. Or maybe 500GB x2 instead of the 1TB?

So how would YOU divide 500GB (x2) & 1 TB for a new install?


Using storage groups

/ 10 GB
swap 1 GB
/mythtv/recordings/500A/   (Rest of 1st 500GB drive)
/mythtv/recordings/500B/   (2nd 500GB drive)
/mythtv/recordings/1000A/  (1TB drive)

---

### Post by nickrout on 2008-06-30
> **tgm4883 said:**
> Using storage groups

/ 10 GB
swap 1 GB
/mythtv/recordings/500A/   (Rest of 1st 500GB drive)
/mythtv/recordings/500B/   (2nd 500GB drive)
/mythtv/recordings/1000A/  (1TB drive)

unfortunately mythbuntu doesn't use /mythtv by default. It buries it in /var/lib/mythtv

Also your setup leaves precious little room for music and videos, both of which you may want plenty of room for (depending how you want to use your system)

mythbuntu does a poor job of default paritioning on a new system, by putting everything in / 

Someone should fix that, and redo the default storage areas to something sensible like /myth (like on knoppmyth).

Also you will not need a large /home directory.

---

### Post by rnelson0 on 2008-06-30
I agree with nickrout. Mythbuntu doesn't do it file structure very well. I guess I should also clarify my storage requirements. The structure the tgm4883 proposed was not ideal, for my needs. Beside recording TV, I also have lots of videos, musics, pictures, and video games that require lots of storage as well.

I was kind of hoping to get some creative ideas for partioning, not just mapping all my space to the recordings folder. For example, after posting this, one of my initial thoughts was this:

500 GB (1)
/boot (100mb)
/(8gb)
/swap (2gb)
/<mythrecordings directory> (rest of the space on this drive)

500 GB (2)
/home/<mythuser>/Music
/home/<mythuser>/Pictures
/home/<mythuser>/Games
etc.

1 TB
/home/<mythuser>/Videos (this is where I store all my videos not recorded by MythTV)

The idea here would be to have a drive to record to that would be separate from where I store most of my files, to reduce lag. I could also have a user job that moved recordings to the 1TB drive after recording was finished. Ideally, I wouldn't want to worry about my machine recording high quality video to the same drive that I'm trying to watch a video file from, ya know?

So if anyone has any better ideas, please share!

Thanks to those that replied!

---

### Post by tgm4883 on 2008-07-01
I did what was asked of me.


Ideally, you would want a smaller drive just for the system files (/)

---

### Post by mrand on 2008-07-01
> **rnelson0 said:**
> I agree with nickrout. Mythbuntu doesn't do it file structure very well. I guess I should also clarify my storage requirements. The structure the tgm4883 proposed was not ideal, for my needs. Beside recording TV, I also have lots of videos, musics, pictures, and video games that require lots of storage as well.

I was kind of hoping to get some creative ideas for partioning, not just mapping all my space to the recordings folder. For example, after posting this, one of my initial thoughts was this:

500 GB (1)
/boot (100mb)
/(8gb)
/swap (2gb)
/<mythrecordings directory> (rest of the space on this drive)

500 GB (2)
/home/<mythuser>/Music
/home/<mythuser>/Pictures
/home/<mythuser>/Games
etc.

1 TB
/home/<mythuser>/Videos (this is where I store all my videos not recorded by MythTV)
Wow!  500 GB is a lot of Music, Pics, and Games.  Even at 10 MB for every single item, that's 50k of those.> The idea here would be to have a drive to record to that would be separate from where I store most of my files, to reduce lag. I could also have a user job that moved recordings to the 1TB drive after recording was finished. Ideally, I wouldn't want to worry about my machine recording high quality video to the same drive that I'm trying to watch a video file from, ya know?<...> While I'm not personally running Hi-def, SATA drives should have no problem with reading and writing *multiple* HD streams: Even if the stream was 50 Mbit/sec, you are only talking about 6 MByte/sec.  Even the worst SATA drives easily do 5x that.  Newer driver are 10x to 20x.  Now, maybe the controller or something else in the chain would be a performance barrier, but I doubt that as well.  So I'd personally not use this as a criteria for partitioning.  Instead, think about future plans - might you use this as a file server and need more space for /home?  Even still, I don't know that I'd do the partitioning all that different than you (for your needs).  If it were my system, I'd likely put the 500 GB drives in RAID 1 and leave the 1 TB drive for videos, music, etc (which I would leave stored on <mythrecordings>).  But again, I don't have 50,000 media files.

[INDENT]Marc[/INDENT]

---

### Post by yonkiman on 2008-07-01
> **rnelson0 said:**
> Right now, I have two 500 GB drives that are LVM'd into one drive...I'll also be buying a new 1 TB drive to add to the mix. Or maybe 500GB x2 instead of the 1TB?

So how would YOU divide 500GB (x2) & 1 TB for a new install?

Have you thought about RAID5?  That would give you a total of 1.5TB of storage, and if any one of your drives failed you wouldn't lose a thing.  I'm about to build a new backend, and I've got 3 750GB drives that I plan to configure for RAID5.  I'm still trying to figure out the best way to partition that 1.5TB, though, so I'm interested in this thread...

---

