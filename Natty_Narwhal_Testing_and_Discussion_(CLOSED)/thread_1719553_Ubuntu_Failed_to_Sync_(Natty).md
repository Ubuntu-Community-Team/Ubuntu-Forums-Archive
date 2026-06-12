---
title: "Ubuntu Failed to Sync (Natty)"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by RichieB07 on 2011-04-01
I just started up Ubuntu One on my netbook, which is running Natty, and it had a failed sync.  

I attached a picture below of the failure.

Any help?

---

### Post by Blasphemist on 2011-04-02
I also have the same issue with Ubuntu One and Natty. I first noticed, just as always seems to happen with new version upgrades, that syncing that I had previously turned off tried to start up again but never actually sent any files. In an effort to get that sync to stop, I eventually went to Ubuntu One via my browser and dinked around to get the darn thing stopped since I couldn't seem to get the folders to recognize that I didn't want them synced (I long ago filled my 2GB).

I didn't care enough about this to file a bug or see if others had. My bad. I should have. I had started to wonder if the issue is a mismatch between my local login and my Ubuntu One login. The password is slightly different. I'll test matching them and report back.

---

### Post by Blasphemist on 2011-04-02
I don't think the password mismatch was the issue. Oh well, was just a quick guess. I guess this is a good thing to be asking in this forum.

---

### Post by RichieB07 on 2011-04-02
My passwords are slightly different too, I wonder if that could be the problem.  I've never synced a single file to it and only recently set it up.  I did it on my laptop that has Maverick, but that shouldn't be a problem since it's supposed to cross sync anyway.

---

### Post by Blasphemist on 2011-04-02
I changed my password to Ubuntu One to the same as my laptop, still the same. I also used Ubuntu One last in Maverick. 

I see that in my efforts to get the never ending sync message stopped, I no longer have files on the Ubuntu One cloud. Now I can't seem to add my computer. The instructions I've found so far don't include doing this in Natty. I'll keep looking

---

### Post by RichieB07 on 2011-04-02
Thanks.  I wonder if it's because it's on Natty, maybe they haven't updated the coding and will do so one the 28th.

---

### Post by Blasphemist on 2011-04-03
I spent some time working on this today but didn't figure it out. I tried to find a log that would help. I spent some time on IRC asking for help. IRC was a pretty good experience today. Learned some and helped some.

In synaptic I do have the ubuntu-sso 1.2.0 package. I do get this error when I reload the package information.
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220

I don't see any report other than ours of this issue. If I don't find something tomorrow I guess I'll add a bug report.

---

### Post by Blasphemist on 2011-04-03
I found the fix to my package public key error, doesn't seem to have changed my ubuntu one sync error. Darn

---

### Post by Blasphemist on 2011-04-03
I know this is a windows habit but I gave it a try anyway. After fixing my package public key error I restarted my computer. I now notice that even before I run the Ubuntu one client the icon has a line across it (it doesn't immediately but I suppose does after it starts trying to sync).

Anyway, still the same issue.

---

### Post by RichieB07 on 2011-04-04
I'm guessing this is just an issue with Natty for the moment.  It'll probably be fixed come the 28th when it's released.  Although it's weird that Natty is in Beta and this still isn't working.

---

### Post by Blasphemist on 2011-04-04
I decided this weekend that from running my laptop since karmik as a newby and installing and tinkering with nearly everything that I would do a new clean install of Natty and in the process shrink my Win 7 partition since it takes 2/3 of my drive space. But, win 7 was friendly enough to leave something unmovable (so far) at the end of its partition and would only let me have less than 2 GB.

I'd been fighting this issue and as you know not getting anywhere. I'd also started using unity when I first went to natty, then went to classic and then switched back to unity. Each of those switches was due to not being able to get the environment to work as I wanted.

The other issue I had was a monitor issue that I'll start a new thread on since I still have it but have learned some things about it. I will tell you that it is that my laptop monitor doesn't respect the top boundary for placing windows but does for the panel, depending on the resolution setting of my external monitor.

The good news is that, low and behold, ubuntu one now works fine. I did the new install from dvd with the option to wipe out the existing natty install. I had backed up home and have copied back documents, pictures and music. I still have the rest if I need it. So whatever the ubuntu one issue was, it was local. 

If there is anything else you think I can offer, do say so. I do have my doubts that you will get help here to get ubuntu one fixed or by getting updates, sorry to say. We've been at it in here for a few days but maybe someone will jump in that can solve it.

---

### Post by RichieB07 on 2011-04-05
I did just do an upgrade, so that might be the problem.  When the full version is released I'm going to a clean install of Natty on the netbook.  By then the problem should be solved.  It was probably just something with the upgrade that's doing it.  But thanks for all the help.

---

