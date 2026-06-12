---
title: "Typical Upnp Problem"
date: 2008-09-08
forum: Mythbuntu
---

### Post by Omega740 on 2008-09-08
Hi guys here are my specs before any info is given.
-Hauppage PVR 250
-AMD Sempron 3000
-2 gigz of Kingston ram
-2 60 gig hitachi HD's 
-1 Ati Radeon x700 (Yes I have already loaded the drivers)

I've been trying to work on this problem on my own on and off for a few weeks now reading up on similar scenarios.  I installed Mythbuntu no problem and set up my video outs.  I also set up the schedules direct portion and mapped out the channels.  I'm wanting to make a rig that can be my Front/Back mythtv setup.

My problem is, is that I can't get mythtv to work. Whether it's the front end or backend tells me that "No Upnp backends found" then it takes me to the database setup which inevitably fails when I load up the default settings and says it "cannot find (ping) database host on the network"

I've looked around for the similar problems and I think I've ruled out a one possibility.

-A user had a problem w/ his old log files being to large and hence ate up all the HD space (my setup is fresh)

I am assuming it has something to do w/ mysql and a database that wasn't initially initialized.  So I did some research on how to create a data is mysql so that I could route both ends to mythconverg.  After a few hours I ended up with nothing but a ERROR 1064 (42000) that recommended to read some nomenclature on my OS setup and what not (basically the run around).  I am new to the linux movement and have found my experience w/ help guide and trouble shooting to be "less" user-friendly than most.  If anyone has any suggestions I would be much obliged.

---

### Post by Omega740 on 2008-09-09
I would post a screen shot of what the mythfiledatabase but w/ my nubness to Linux and 35 mins of research I can´t even pop out a screen shot.  I would just like to say that I don´t know what Xfce was thinking when they didn´t implement typical defualt keyboard shortcuts into their program such as Print Scrn.

---

### Post by Cyrixxal on 2008-10-04
I have been having this issue as well. I had with an old install and a fresh install.

I have searched, searched, and searched... None of the solutions are remotely applicable..

Has anyone had any success on figuring this out?

Cyr

---

### Post by Eric Boring on 2008-10-05
I had the exact same problem on a brand new install of Mythbuntu 8.04. Try removing and reinstalling mythtv-backend.

Also, I don't know if this is related to the problem, but I have a note in my project notebook that I removed myth-backend-master. If you are not going to be using other backends, you might try removing that too, if reinstalling the backend doesn't help.

Good luck.

-Josh

---

### Post by dcwdrum on 2008-10-05
Hi there,

I ran into this same problem when I upgraded to 8.04.  After some searching around I found this thread  [http://ubuntuforums.org/showthread.php?t=793783&highlight=UPnP+backends+found](http://ubuntuforums.org/showthread.php?t=793783&highlight=UPnP+backends+found)

The code that worked for me was this:

```
sudo dpkg-reconfigure mythtv-database
```

Make sure that you enter the proper root user and pass when you do this. This will create the user and will fix the "No Upnp backends found" problem and enable you to run the backend setup.

Check out the link above for more information.

Thanks,

~Dana

---

