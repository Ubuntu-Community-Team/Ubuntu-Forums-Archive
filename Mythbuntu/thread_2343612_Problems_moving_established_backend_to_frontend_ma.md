---
title: "Problems moving established backend to frontend machine"
date: 2016-11-17
forum: Mythbuntu
---

### Post by bernard2 on 2016-11-17
Hi all - I've been using MythTV successfully for several years, most recently with 0.27.4 on Ubuntu 14.04, with a two machine set up: the backend ("myserver") is also a file server, the front end ("myhtpc") is also an HTPC.

For various reasons (mainly location of TV aerial!) I now need to shift the MythTV Backend function to the other machine, so it will be acting as both MythTV FrontEnd and MythTV Backend. However, as the HTPC is a silent machine with only a small SSD for storage, I want to keep all the files stored on the old backend.

I thought this would be so easy! Having consulted numerous discussion threads and also the wiki (eg [https://www.mythtv.org/wiki/Database_Backup_and_Restore](https://www.mythtv.org/wiki/Database_Backup_and_Restore) ) I first of all made sure that, on myhtpc, I had access through Samba shares to the myth storage directories on myserver - with the same path names.

Then, on myserver, I took a fresh database backup and tried to shut down the backend (I may not have been successful - I've had a lot of trouble getting it to die in the past).

Moving over to myhtpc, which already had the MythTV Backend installed but never used, I then used mythconverg_restore to import the database - including drop_database - and then ran myth_converg with change_hostname so that (I thought) myhtpc would now have a fresh, up to date database but with the name changed. First problem: if I ran this last command specifying the hostname, I got duplicate errors. If I ran it specifying IP address, it ran but seemed not to be changing anything.

On myhtpc, I ran the MythTV Backend setup. I was able to set storage directories to point to the shared storage area. I changed the master backend IP address to myhtpc's, and everything fell apart.  I note that this change got communicated (not by me!) to myserver, so MythTV Backend setup there saw the same address.

I've now managed to roll things back so that myserver is the master backend again, but I therefore haven't achieved what I want, which is to be able to move my tuner card(s) over to myhtpc.

Clearly I don't fully understand what's going on here, and I'm hoping that there is a simple sequence that I can follow that will get me where I want without, obviously, losing all of my data!

Can someone please give me some pointers?

---

### Post by bernard2 on 2016-11-18
In the absence of any suggestions, I'll add what I've been up to today. I gave up on trying to make the existing Mythtv installations work, and (after taking backups!) went for a more destructive approach. I've disabled mythbackend on "myserver", so it is now just a Samba file server. I removed all Myth elements from myhtpc, and did a fresh install of the current version (0.27.6+fixes). Copied in the database backed up from before, (with automated schema update), changed hostname ... and it's still not working. To be honest, I've messed this installation around so much I think I'll have to rewind and start again. 

Admittedly there was some time spent on a diversion of getting the tuner card driver sorted out (done now) but this is taking a long time...

---

### Post by bernard2 on 2016-11-21
Not sure how! Kept repeating the process until it stuck but eventually I got a backend that would run, with data imported.

---

