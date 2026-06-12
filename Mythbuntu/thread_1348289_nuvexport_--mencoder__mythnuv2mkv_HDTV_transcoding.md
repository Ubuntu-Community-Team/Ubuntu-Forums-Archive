---
title: "nuvexport --mencoder / mythnuv2mkv HDTV transcoding speed"
date: 2009-12-07
forum: Mythbuntu
---

### Post by JBaugh on 2009-12-07
I have three mythtv backend machines which I believe are set up the same, but which I am getting very different results as far as transcoding using nuvexport or mythnuv2mkv.

All are running ubuntu 9.10 / myth 0.22
nuvexport version:  0.5
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2
MEncoder UNKNOWN-4.4.1

Machine 1 (Master Backend - setup 1):
-Computer-
Processor		: 4x Intel(R) Pentium(R) D CPU 3.20GHz
Memory		        : 4055MB (684MB used)
Operating System	: Ubuntu 9.10
User Name		: matt 
Date/Time		: Mon 07 Dec 2009 01:39:38 AM CST

Machine 2 (Master Backend - setup 2):
-Computer-
Processor		: 4x Intel(R) Core(TM)2 Quad CPU    Q8300  @ 2.50GHz
Memory		        : 4057MB (1200MB used)
Operating System	: Ubuntu 9.10
User Name		: jon
Date/Time		: Mon 07 Dec 2009 01:44:01 AM CST

Machine 3 (Secondary Backend - setup 2):
-Computer-
Processor		: 2x Intel(R) Core(TM)2 Duo CPU     E7500  @ 2.93GHz
Memory		        : 4057MB (849MB used)
Operating System	: Ubuntu 9.10
User Name		: jon
Date/Time		: Mon 07 Dec 2009 01:44:57 AM CST




Machine 1 performs as I would expect - 25 - 50 fps using 90-100% of the cpu (all cores utilized)

Machines 2 and 3 transcode at no more than 3 fps and utilize <30% of the cpu (1 core).



Does anyone have any idea where I may look to see what is causing this?  

I am completely out of ideas.

Thanks,
-Jon

---

### Post by JBaugh on 2009-12-17
Looks like everyone is just as confused as me?  :)

---

### Post by SiHa on 2009-12-17
OK, wild stab in the dark.

I think I recall from when I was playing with nuvexport that the mencoder command line that it spits out uses the **nice** command to adjust it's priority. IIRC, it was **nice 16** which is almost the lowest priority.

It could be that somehow the kernel isn't quite getting it right on the two slow machines.

Maybe have a look at the commmand line being generated (by running nuvexport from the terminal), then try adjusting the niceness level. It can range from -20 (Highest) to 19 (Lowest).

Now it may be that a process will still use 100% CPU time, even with a low priority, if nothing else wants it. I don't know enough about Linux to say for sure, but I thought I'd throw it in, as no-one else has offered anything in the last week.

---

### Post by silverdulcet on 2010-01-22
I am experiencing the same problem. This is after I upgraded to Mythbuntu 9.10. I used to get around ~30-60fps during the first pass on an OTA ATSC to Xvid/AVI transcode. This is using mythnuv2mkv which makes use of both transcode and mencoder. 

Anyone have any ideas on what to look into to fix this? Did you happen to solve your problem JBaugh?

---

### Post by JBaugh on 2010-02-06
No, I never did solve my problem... I took the lazy man's way and bought a couple new hard drives.   

I never got back to this particular project, but it's a Saturday afternoon and I've got nothing else going on, so I'll try again and post my results if I come up with anything.

-Jon

---

### Post by silverdulcet on 2010-02-06
> **JBaugh said:**
> No, I never did solve my problem... I took the lazy man's way and bought a couple new hard drives.   

I never got back to this particular project, but it's a Saturday afternoon and I've got nothing else going on, so I'll try again and post my results if I come up with anything.

-Jon

I was in a hurry to make use of a new Nvidia GT 220 video card for VDPAU, I used the repos here:
[http://http://avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html]("http://http://avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html") to upgrade my 9.04 installation to Mythtv .22

So I can't be sure, but I think it had to do with the version of mencoder that was in that repo. To solve the problem, backed up my database, did a clean install of Mythbuntu 9.10 and restored my database. Now transcoding is back to the same fps I was getting prior to this.

---

