---
title: "Recordings Thumbnails - can you specify a directory?"
date: 2010-12-23
forum: Mythbuntu
---

### Post by myth01 on 2010-12-23
I've Googled but found surprisingly few (in fact nearly no) matches to this.

I have an SSD as boot drive and 4 1TB hdd's for recordings.  I've set spin-down times with hdparm for the rotational disks (mostly for the sake of noise but also longer life) however any time you browse the recordings list all the disks are spun-up to grab the thumbnails.  Is it possible to specify a different directory to the recordings for the storage of thumbnails?  I would put them on the SSD for responsiveness and to save the hdd's.

I've had a look at the storage groups trying to find 'Thumbnails' but didn't see anything that looked related...

(mythbuntu 10.04/mythtv 0.23.1)

---

### Post by ian dobson on 2010-12-24
Hi,

Sorry you can't do this, the thumbnails are always saved to the same directory/storagegroup as the recordings.

Regards
Ian Dobson

---

### Post by myth01 on 2010-12-24
Thanks Ian, I feared as much.  I wonder if this is something that would be popular enough for a patch/change?

In the mean time maybe I need a workaround.  I know a simple test would tell me, but does it matter if the thumbnail for a specific recording is not on the same drive/in the same folder but still in the same storage group?

I'm thinking that if I moved all of the thumbnails to one of the 1TB drives (and wrote a script to do that for new recordings), then only that 1 drive would be spun-up.  Would that work or does myth actually scan the recordings as well as the thumbnails?

Matt

---

### Post by ian dobson on 2010-12-24
Hi,

A patch might be a good idea, I thing myth mainly just uses the information in the mysql database and only reads the thumbnails when necessary. The frontend actually has a thema cache under home/username, so maybe if the problem is that the frontend is causing the drives to powerup, moving home to the ssd might help.

Regards
Ian Dobson

---

### Post by myth01 on 2010-12-24
/home is already on the SSD but cheers for the suggestion.  I might give moving all of the thumbnails to just 1 of the drives a try first.  If I heard correctly when I was testing it last night; as I scrolled through the recordings list, and hence requesting thumbnails, you could hear the individual drives being spun-up at different times suggesting it was 'on-demand' based on where the thumbnails were stored...

I have been looking for an opportunity to learn C++ and contribute something back to mythtv.  I did a lot of C many years ago (sadly nearly all forgotten, and all Windows GUI based) but would like to get stuck in...could be a while before I have anything ready though!

---

### Post by uncle hammy on 2010-12-24
That doesn't work.  If it doesn't find the thumbnail in the folder with it's "owner", it recreates it.  I just tested.

---

### Post by myth01 on 2010-12-24
Hi uncle hammy, yeah I just tested it too and had the same results (unsurprisingly).

Looks like I've found something to do over the holidays...

---

### Post by myth01 on 2011-01-03
In the end I moved all of the TB disks to a new fileserver that the backend can access over NFS.  The server is in an Antec 300, brilliant case but with 4 120mm+ fans it is NOISY but at least it's in a different room.  The FE is now very very quiet.

---

