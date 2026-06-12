---
title: "Zonbu first issue - Via processor"
date: 2007-10-10
forum: Mythbuntu
---

### Post by packet on 2007-10-10
Well it looks like the x86 via Esther processor is not compatible with the default 686 build image that Gutsy is shipping with.  This is possibly not correct but this bug in Edgy leads me down that path:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59338](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/59338)

Although the version is different and the processor is different I'm nervous about it.  I may have to go with the "alternate install cd" and start out with the xubuntu, then do the "install mythbuntu from an exisitng install"

Maybe this is something else I'm running into or an error on the CD I pulled from (I downloaded both the 64 and 32 bit versions).  The only think that makes me wonder is that I booted my laptop off of it just fine.  Booting up this new system gives me an error: Your CPU does not support long mode.  Use a 32bit distribution.  Which makes me wonder if my work laptop actually has a 64 bit chip in it!

---

### Post by dannyboy79 on 2007-10-10
well I don't think that chip is a 64 bit chip is it? If it's not than you definitely can't go with 64bit Ubuntu. According to the bug report, it's not going to work with the 686 kernel image either. Why don't you just use the 386 kernel image or compile your own. It's not hard, just be sure to enable what you need enabled when compiling your own kernel. here's a great guide for kernel compilation:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by packet on 2007-10-10
Ok, I did accidentally grab the 64 bit version and my laptop does actually have a 64 bit chip in it!

So got the zonbu fully loaded, had to futz with the bios a bit before it would boot off of a USB drive.  Once it booted up the install recognized the 4gb flash drive to install to and I was off and running.

Now I just need to fix and issue with the backend using 127.0.0.1 instead of its actually IP which is needed for remote frontends.

---

### Post by dannyboy79 on 2007-10-11
under the general section when you enter mythtv-setup. I would make sure your ip is staticly assigned.

---

### Post by packet on 2007-10-11
Well, after changing the IP in the Backend to be its eth0 ip instead of 127.0.0.1 I connected no problem only to find that my video was horrible.  Then began the horrible saga of trying to complile the VIA CX700 drivers which is still a saga in process.  I did get it to compile correctly but it wouldn't copy the files to the correct locations, so I copied them manually but X fails saying that there is something unrecognized in the via driver.  This is odd as I compiled it on the machine in question so I'm not sure why it wouldn't work.  I may have to downgrade to dapper drake and try it with that, then load my own mythfrontend setup on that.  I'd hate to lose the bells and whistles provided by mythbuntu though.

Anybody with any success with Gutsy and the via CX700 drivers?

---

### Post by superm1 on 2007-10-12
> **packet said:**
> Well, after changing the IP in the Backend to be its eth0 ip instead of 127.0.0.1 I connected no problem only to find that my video was horrible.  Then began the horrible saga of trying to complile the VIA CX700 drivers which is still a saga in process.  I did get it to compile correctly but it wouldn't copy the files to the correct locations, so I copied them manually but X fails saying that there is something unrecognized in the via driver.  This is odd as I compiled it on the machine in question so I'm not sure why it wouldn't work.  I may have to downgrade to dapper drake and try it with that, then load my own mythfrontend setup on that.  I'd hate to lose the bells and whistles provided by mythbuntu though.

Anybody with any success with Gutsy and the via CX700 drivers?
CX700 drivers? These aren't supported by openchrome?  Have you tried?

---

### Post by packet on 2007-10-13
So the CX700 drivers are only partially supported by the experimental version of OpenChrome.  No MPEG decoder support and no 3d support, but since my trials and tribulations to get the via code working on my system have failed miserably I've given up and went back to the experimental unichrome.

And the results are very positive, my cpu went down from 80-90% to 30% to 40%, so now I've got a fairly viable mythfrontend system.  The family has been using it for a couple of days and except for some remote issues, screen blanking, and odd resolution issues with my 32" LCD TV its going well.

I'm hoping the final version may fix the screen blanking and I've already fixed the remote, I had to add in a bunch more options for mplayer and fix a few oddities in the overall lirc config for myth but now its better than ever.

Now its time to rebuild my mythdora combined frontend/backend into a mythbuntu backend only system.  Gotta figure out if its easy enough just to move files and backup/restore the DB.

---

