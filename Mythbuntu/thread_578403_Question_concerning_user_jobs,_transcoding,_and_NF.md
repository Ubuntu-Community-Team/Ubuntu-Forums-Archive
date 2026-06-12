---
title: "Question concerning user jobs, transcoding, and NFS storage"
date: 2007-10-17
forum: Mythbuntu
---

### Post by jakev383 on 2007-10-17
I have a working system - even survived the SD update. My master backend is a MythDora install, I have another MythDora install in the living room, and a Mythbuntu install in the bedroom.  I dropped the mythtv mailing list a while back (got tired of 300+ posts a day complaining about SD). 
Anyway, I also have a home server that has 1T of storage. I've already set up a NFS share on it, and have the NFS share mapped as /mnt/videos on the frontend.
I also have been manually using the Job Options -> Begin Transcoding -> Low Quality to cut the commercials and transcode my shows - that's great! A 2.2G show gets edited and shrunk down to ~500M.  Love it! I run it manually to make sure the cut points are in the correct spots.
Anyway, once I'm done transcoding the show, I'd like to have it moved to my /mnt/videos folder instead of staying on the backend (only a 250G drive). I've read some about user jobs, and google'd a bit, but that only seems to confuse me more - I don't need to transcode it for my PDA, and I'm not having a problem (since I'm not using it yet) so 99.9% of the results do not apply to me.  I think this whole process has to be done at once (at least, easily), so I have a bunch of shows that are ready to be transcoded and moved somewhere else.  
I'd also like this to be easy for the wife to do as well - she could just select the job to be run, and then wander off.  Can anyone explain it to me easily? I can handle 2-syllable words, but I'm not a perl programmer by any means - I'm like a bad comedian when it comes to perl - I know enough 1-liners to get by.
Thanks in advance everyone.  Guess it may also help, but I'm running myth 0.20.2-164.

---

### Post by superm1 on 2007-10-17
> **jakev383 said:**
> I have a working system - even survived the SD update. My master backend is a MythDora install, I have another MythDora install in the living room, and a Mythbuntu install in the bedroom.  I dropped the mythtv mailing list a while back (got tired of 300+ posts a day complaining about SD). 
Anyway, I also have a home server that has 1T of storage. I've already set up a NFS share on it, and have the NFS share mapped as /mnt/videos on the frontend.
I also have been manually using the Job Options -> Begin Transcoding -> Low Quality to cut the commercials and transcode my shows - that's great! A 2.2G show gets edited and shrunk down to ~500M.  Love it! I run it manually to make sure the cut points are in the correct spots.
Anyway, once I'm done transcoding the show, I'd like to have it moved to my /mnt/videos folder instead of staying on the backend (only a 250G drive). I've read some about user jobs, and google'd a bit, but that only seems to confuse me more - I don't need to transcode it for my PDA, and I'm not having a problem (since I'm not using it yet) so 99.9% of the results do not apply to me.  I think this whole process has to be done at once (at least, easily), so I have a bunch of shows that are ready to be transcoded and moved somewhere else.  
I'd also like this to be easy for the wife to do as well - she could just select the job to be run, and then wander off.  Can anyone explain it to me easily? I can handle 2-syllable words, but I'm not a perl programmer by any means - I'm like a bad comedian when it comes to perl - I know enough 1-liners to get by.
Thanks in advance everyone.  Guess it may also help, but I'm running myth 0.20.2-164.
Well personally i think this is your best bet:

After items are transcoded have a job run through and **copy** the file to your nfs mount.  This way you can let the backend autoexpire the file at your leisure and not need to muck with mysql database deleting and such.

---

### Post by jakev383 on 2007-10-18
That sounds like a great idea - I was thinking of having it copy them to the NFS share, then I would have to delete the from the regular list or let them expire.
I'm just a little confused as to where I would put the script, and how I would get it to run. Can you offer some light on that subject? Would I write a script and run it as a  User Job? I'm trying to get VNC or vino working on my backend now, since it is headless and it's a paint to drag a monitor over there to work locally.
Thanks for the reply!

---

### Post by superm1 on 2007-10-18
You'll pop it in /usr/local/bin.  Mark it executable with chmod +x.  It then needs to be enabled as a user job.

Mythbuntu provides an option for VNC in the control centre and during installation.  Alternatively you can X forward mythtv-setup.

---

