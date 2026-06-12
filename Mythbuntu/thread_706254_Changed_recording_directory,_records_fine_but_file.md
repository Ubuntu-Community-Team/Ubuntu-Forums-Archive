---
title: "Changed recording directory, records fine but files not listed in Media Library"
date: 2008-02-24
forum: Mythbuntu
---

### Post by daviding on 2008-02-24
I've had a relatively smooth installation of Mythbuntu 7.10 x86_64, but now have a puzzle.

I started with a clean 500GB SATA drive on a new computer, creating three partitions.  The biggest partition (most of the disk) is named home, and I formatted it as JFS.

When I went through the original installation, the Directory to hold recordings ... was set to /var/lib/mythtv/recordings ... which I discovered was the small (first) partition.  I changed the Directory to hold recodings to /home/mythtv .

I was getting messages that /home/mythtv wasn't writable, so I did a chmod to match the original directory.

The recordings are now working fine, but there's two issues.

(1) Scheduled recordings aren't showing up in Myth Front End under Media Library ... Watch Recordings ... although the LiveTv I watch is there.

(2) In Manage Recordings ... Delete Recordings ... the shows that were in the old var directory still show up, even though I've deleted them.  The shows in the new directory don't show up.

If I look at Manage Recordings ... Previously Recorded, I can see a show where the MPEG exists in /home/mythtv , but this is a show that isn't listed under Media Library ... Watch Recordings.

Can someone suggest a configuration step that I've left out?  (I presume that to clean up records from the old directory, I may have to go into MySQL).  Thanks.

---

### Post by newlinux on 2008-02-24
So the scheduled recordings are being recorded, but just not showing up in your Watch Recordings listing? Have you made sure your group filter is set to all Programs (Press "m" for menu when you get to the watch recordings screen)?

For 2, you could delete the records in mysql as you suggest (I think you could just delete the appropriate records in the "recordings" table). or you could create files with the same names as teh recordings that myth thinks you still have but you've deleted (you'll see the filenames that myth is trying to delete in your logs) in your recordings directory. Go into your recordings directory and do something like:

```

touch 1051_20080208220000.mpg 

```

for each "ghost" recording filename. Then go delete them. Make sure permissions are such that myth can delete the files you create.

---

### Post by daviding on 2008-02-24
Thanks for the pointer to filters.  I didn't know about that.

I know that the user interface is designed for use by remote control ... but I'm finding it an annoyance from a computer keyboard.  I guess I'm in that in-between transition, and I'm trying to understand how television and computer technology are converging.

---

### Post by newlinux on 2008-02-24
yeah, I much prefer the remote, since I use it for all other parts of my Home theater system. for things done by keyboard on the computer I usually  ssh in or VNC in. Manipulating the user interface with a keyboard would require more memorization of what keys mean, instead of mapping them to common remote control keys.

---

