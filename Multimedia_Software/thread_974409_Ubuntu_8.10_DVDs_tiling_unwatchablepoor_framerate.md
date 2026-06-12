---
title: "Ubuntu 8.10 DVDs tiling unwatchable/poor framerate"
date: 2008-11-07
forum: Multimedia Software
---

### Post by Kusho on 2008-11-07
I'm searching thru here to find fixes, but this is a odd topic to search on.  This problem has me debating rolling back to 8.04 or searching for another flavor of Linux/ or completely giving up and going back to Win98...  Short term probally figure out how to do a multiboot and get that going...

That all said, I'm using an ancient P2 Motherboard/ P3 550 Processor, 640 MB of ram, Vodoo 5500 videocard, (and look at my other posts to see how videocard is setup, as had to ask how to get that working..

With Ubuntu 8.04 DVDs would play and I could actually watch.  I'm curious if this is one of those 8.10 phasing out video cards type of issues...  

Now when I try and play a DVD in either VLC or Todem it skips, audio skips, pixilation...  we'd call this tiling in the industry.  Horrible tiling.  I know this is an older PC...  but this comes down to usability for me.  I'm listing out the things I can do in Ubuntu...  vs Win98 and the list is getting shorter...  I can surf, and love that I can use the newest Firefox.  I have to use the old crappy IE with win98...  no tabbed browsing for me.  But thats about it. I can surf, and stream radio.  No decent games will run...  and it's funny as the only games I see that work well in Ubuntu anyway are all the old ones that were wrote for my Videocard...  Guessing that might be more of a learning curve thou...  Haven't got Wine running yet...  etc...  etc...  but with 8.04 I could atleast watch DVDs and Flash movies.  Flash movies are also giving me framerate issues, but I'm using the new Adobe Flash 10 and I'm seeing posts that say that is an issue with it, so I need to figure out how to change versions and either roll back on it or switch to gnash...

But I'm using both VLC and Todem and DVDs are worse than streaming flash movies...  They cut out soo bad there is no way to even get thru one preview.  and with Ubuntu 8.04 it wasn't this bad.  Anyway...  if anyone has any idea what I can try let me know.  Thanks.

---

### Post by Kusho on 2008-11-09
2 days and no one else to answer my dilemma.  I'm going to go ahead and roll back to 8.04 tomorrow and see what that does for me.  Also thinking of trying Kubuntu and seeing what I think of that interface and if it helps at all.

---

### Post by celem on 2009-02-06
I was searching for the same basic issue and noticed your post. The poor video issue may drive me back to XP. I suspect that the issue has more to do with Nvidia's driver than with Ubuntu 8.10 itself, but regardless of the cause, it makes Linux significantly inferior. I have an in-progress project whereby I'll continue with Ubuntu until this summer, when my project should be completed. If I cannot resolve to poor video issue by then, I will switch back to XP. The issue is frustrating. I can watch most Youtubes fine, yet embedded links to Youtube oftem have tearing. Other Flash videos, such as hulu.com exhibit erratic play with frequant halts.  Wwv video files play very poorly in totem yet play fine with VLC.

---

### Post by KEE on 2009-02-06
Well i hope you find out how to fixit. the Ubuntu community will be very happy if you do :) i hate this issue its happens with all those types of links on youtube and others site very often. Good luck on your project :)

---

### Post by cariboo on 2009-02-06
Intrepid uses a newer version of xserver and the driver may not have kept up with the new server. If Hardy works better for you, why not change back. Use what works best for you.

Jim

---

### Post by driven1 on 2009-02-06
I'm having the same problems with ati graphics. Earlier installs worked fine, but now no video is watchable. I've tried multiple file types and multiple apps. All my codecs are up to date, still no joy.
I'm also looking for a solution that does not involve going back to Hardy as I need some things that are much easier in Intrepid. If I happen across something, I'll report back here.

---

### Post by markbuntu on 2009-02-06
The new 9.1 fglrx driver from ati fixed all the video watching issues I have been having with my ati HD3650. If you are using an earlier version of the propietary ati driver you should set all the preferences in your applications to use X11. That will improve performance significantly.

To the OP. There is a limit that old hardware can be supported as new features are introduced, the hardware just cannot support them. Vista is a prime example of that, they just lopped off most of the pcs built in the last 10 years. Ubuntu is also moving along and painful decisions must be made about keeping support for old hardware that just becomes more and more difficult to get to work with newer features that are being incorporated into the core processes. The old hardware is just incapable of supporting this so must be dropped along the way for further progress to be made. Should I complain that my P133 laptop cannot run Intrepid?

It is actually quite astounding that Hardy worked as well as it did with that old hardware. A P2 with 640MB of ram is near the minimum requirement. It seems Intrepid has pushed the threshold a little higher.

Face it, you cannot be on the bleeding edge anymore with that hardware and you should defintely do not even consider upgrading to Jaunty 9.04 unless you switch to xubuntu or get a newer machine.

---

