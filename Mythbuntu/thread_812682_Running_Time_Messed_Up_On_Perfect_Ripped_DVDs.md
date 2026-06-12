---
title: "Running Time Messed Up On Perfect Ripped DVDs"
date: 2008-05-30
forum: Mythbuntu
---

### Post by ab1301 on 2008-05-30
I have ripped a bunch of dvds on the perfect setting in myth.  When I play back the vobs in the internal player, the running time on some of them is being reported as way shorter than the movie actually is.  The whole movie is there, so I can watch it all, but the mis-reported running time wreaks havoc with the skip function.  Is there any way to fix this?

---

### Post by jakev383 on 2008-05-30
Are you ripping them to a network share (CIFS or NFS)?

---

### Post by ab1301 on 2008-05-30
Um, I don't think so, but I'm not really sure.  I used whatever default file system mythbuntu 8 installs, and I have not specifically set up any sort of network sharing.

---

### Post by jakev383 on 2008-05-30
You're not then. I have the same issue, but mine are ripped to a network share which I believe is causing my problems.
Hopefully someone else can chime in with an answer.

---

### Post by ab1301 on 2008-05-31
Well, after a lot of searching, I think I've determined that the problem is that MythTV is unable to rip valid seek tables from some dvd discs.  I'm really suprised that this is not common knowledge, as I would think there would be a lot of people using mythbuntu to rip vobs from dvds, but maybe not.  

I am now doing some more searching to try to figure out how to repair the broken seek tables...  If anyone can point me in the right direction, I would appreciate it.  I tried mythcommflag --rebuild, but it just gives an error 32.  I am trying mythtranscode --buildindex right now, but its at 755% complete right now, with no signs of stopping.  Odd.  I'll let you know if I get anything to work.

---

### Post by ab1301 on 2008-05-31
After a lot of looking and trial and error, I have come up with something that worked on all but one of the files I tried to fix tonight.  The starting point is the wiki page below.

[http://www.mythtv.org/wiki/index.php/Repairing_the_Seektable](http://www.mythtv.org/wiki/index.php/Repairing_the_Seektable)

I say starting point, because the stuff on that page did not work for me as-is.  First off, they tell you to run 

sudo /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl

I kept getting "command not found."  This may be obvious to more experienced linux users, but for a relative newbie like me, it took awhile to figure out that I had to type:

sudo perl /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl

Once that runs (and you might have to run it a couple times before stuff starts working), they tell you to run mythcommflag --rebuild.  This did nothing for me.

The next step is to run:

 mythtranscode --mpeg2 --buildindex --showprogress --infile <filepath> 

This is incorrect, and will not work for a ripped dvd.  For anything that is not a myth-recorded tv show, you have to type:

mythtranscode --mpeg2 --buildindex --showprogress --video --infile <filepath> 

As a side note, I find that it is easier to cd to the video directory, so that you can just type the file name, rather than the entire path.  That way, you can also hit dir, and cut and paste the name of the file you want.

Well, that's enough for tonight.  I have about a hundred more files I haven't gone through. The seek tables are only broken on a random few, so I'll have to test all of them, and fix all the broken ones.  I wish I understood why this is happening, and what I can do to stop it, as it is very frustrating.  There are some suggestions as to cause on the wiki page, but I can't figure out any concrete preventative steps from those suggestions.

---

### Post by jakev383 on 2008-06-01
Thanks for posting the results and the fix!  I'm sure this will help out someone in the future as well.

---

### Post by Trollslayer on 2008-06-01
> **ab1301 said:**
> I have ripped a bunch of dvds on the perfect setting in myth.  When I play back the vobs in the internal player, the running time on some of them is being reported as way shorter than the movie actually is.  The whole movie is there, so I can watch it all, but the mis-reported running time wreaks havoc with the skip function.  Is there any way to fix this?

Is the playback smooth? Also, how much shorter?

---

### Post by ab1301 on 2008-06-04
yes, playback is smooth.  By shorter, I mean like a whole movie will show as being four or five minutes long.  Or, I have noticed some special features that are only a few minutes long as showing as several thousand minutes long.  Either way, playback goes fine until you try to skip forward or back.

---

