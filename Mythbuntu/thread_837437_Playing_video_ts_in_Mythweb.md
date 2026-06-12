---
title: "Playing video_ts in Mythweb"
date: 2008-06-22
forum: Mythbuntu
---

### Post by Dilligaf on 2008-06-22
I have my dvd collection ripped to hard drives on a server, I can browse the collection in Mythweb but when I attempt to play I get this error:  The requested URL /mythweb/data/video//mnt/server_E/21_GRAMS was not found on this server. I can play recorded TV in mythweb off the same server with no problems and I can play the dvd rips in Myth without any problems. The server has read and write permissions for everyone and is mounted in fstab with me as the owner and mythtv as the group. www-data is a member of the mythtv group. the directory structure is movie_name/video_ts/*.vob, *.ifo, *.bup, the vobs are split into 1 gig files. Has anyone got mythweb playing or streaming ripped dvds ?? Or is this not possible ? Thanks for any help.

Mike

---

### Post by QA_manager on 2008-06-22
I would be happy to test it on my system and tell you my results, but I can't stream any videos (see my post here: [http://ubuntuforums.org/showthread.php?t=836513](http://ubuntuforums.org/showthread.php?t=836513)).

Did you just install Myth and streaming worked, or did you have to do something to make it work?

Streaming ripped DVDs is the next thing on my list of things to do, but first I have to get past the streaming part!

---

### Post by Dilligaf on 2008-06-25
Am I the only one having this problem ? I find that hard to believe. Does anyone have this working?

Mike

---

### Post by QA_manager on 2008-06-26
Now that I have streaming working I will rip a DVD and try it.  Please give me a few days.  

Is there an easy way to rip it on one machine but load it onto the Myth backend?  My backend is in the basement and I have not yet built a frontend.

---

### Post by QA_manager on 2008-07-01
Over the weekend I installed MythTV (frontend only) on a spare system, but I can't get it to rip a DVD.  When I select a program and tell it to rip, it almost instantly says 'Nothing to do.  You could rip a DVD'.

When I exit MythTV it says it is unable to contact the MySQL database - even though the database test worked during installation.

I'm afraid I'm not helping you very much!

---

### Post by Dilligaf on 2008-07-06
Sorry for the slow reply, I've been out of touch with the world for the last week. I haven't tried ripping DVDs in linux, I rip them on a Windows box using AnyDVD and DVD 
Shrink. I'll have to try ripping in Ubuntu and see what I can come up with.

Mike

---

### Post by bmwman on 2008-09-26
I can see all my ripped videos (avi) but can't play it either. I also get the " movie_filename was not found on this server"

---

### Post by Dilligaf on 2008-09-27
I never did get this resolved.

Mike

---

