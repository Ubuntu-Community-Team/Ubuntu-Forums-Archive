---
title: "MythTV + Server -&gt; windows users"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by kochen on 2006-11-14
Hi,
I have this:
[LIST]
[*]A Ubuntu 6.06 running server.
[*]Several Windows machines using the Server's services (Apache, MySQL, etc...)
[/LIST]

What I want is this:
Install a HTPC-like-machine, with Ubuntu 6.10, to have MythTV & transmit TV/Video to all other users...

can this be done?

if not, any other ways on accomplishing this idea...?

---

### Post by superm1 on 2006-11-14
You can set it up so that the users can view the recordings through samba, but live tv won't really be a feasible feature for the windows users.

---

### Post by kochen on 2006-11-14
why not?
will I be able to broadcast liveTV at all? (only inside the local-network)

what & how should I set for this...?

---

### Post by superm1 on 2006-11-14
Well there is no current frontend on windows.  You need to use a frontend to control / tune live tv.  You can schedule programs through mythweb and watch recorded programs.  You can run a frontend in vmware if you want too.  

There was a winmyth project, but it isn't compatible with 0.20.

---

### Post by kochen on 2006-11-14
will a compatible **winmyth** (with .20) solve my problem?

---

### Post by superm1 on 2006-11-14
Yes, if it is released at some point.  I'll warn you though, the live tv interface wasn't very good last time I tried the winmyth project ( .18 ), and it was fairly unstable.

---

### Post by kochen on 2006-11-14
OK, i'll cross my fingers for a soon release.

in the meantime, can you tell me what do I need to set up on the Server Side?

---

### Post by superm1 on 2006-11-14
Start by walking through the edgy guide here to get your machine set up.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by kochen on 2006-11-14
a back-end installation will suffice?
or do I need the front-end as well?

---

### Post by superm1 on 2006-11-14
Well if your looking for a HTPC to sit in your home theatre, you should set up a frontend as well.  Really the cool part that comes with myth is the frontend anyway :) 

Commercial skipping and detection quickly becomes a necessity when watching tv. (at least for me)

---

### Post by kochen on 2006-11-14
you're absolutely right!

what about using the Server's MySQL? is it possible?

---

### Post by superm1 on 2006-11-14
You will only need one MySQL server on the network.  If you've already got one up and running, during mythtv-database installation, there is an option to install onto a remote MySQL server instead of installation to a local mysql server.

You will be asked for the root user name and password of the mysql server as well as the location.

---

### Post by kochen on 2006-11-14
Great, I already have MySQL on the Server machine...


thanks,
I'll pop up some more questions upon installation (I don't have the machine ready yet)

---

