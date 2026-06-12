---
title: "Unable to watch DVDs (Audio Output Unavailable)"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by FrozenFOXX on 2007-04-03
Okay, this has become an infuriating problem that I have not yet found any solution for.

Using Kaffeine under Kubuntu on Edgy Eft I have previously been able to play DVDs.  Now I didn't test it out TOO much as I thought the sound synching was off but at the very least I figured that was probably an engine configuration issue I would deal with at another time.

Recently I am almost totally unable to play DVDs anymore.  I put the disc in and tell Kaffeine to play DVDs (I have already installed libdvdcss, libdvdread, and the like).  It starts to but seemingly as soon as it gets to the film it stops hard and pops up an error message claiming the Audio Output is Unavailble, Device is Busy ().  The message is from Xine so I thought it might be a configuration issue but have yet to find one.

I also installed Mplayer32, Mplayer, and then changed the link from gmplayer to point to the Mplayer32.  I haven't been able to adequately test whether or not there's a sound sync issue with movies played back in Mplayer32 but from what I can tell if there is it's consistent, small, and the movies play just fine (even the WMV9).

If it matters I'm using 64-bit Kubuntu.  I have absolutely no idea where to go from here, all I want is to be able to play my DVDs and back them up (but that latter one is a different story entirely).

---

### Post by sparky64 on 2007-04-03
Hi Just beat me to this post,Have got the same problem.
Whats Happening to me is I have to kill artsd to get menu screen to play.(not every time though)
But as soon as i click on play i get same message.
If you look at system guard there are two 2 instances of kaffeine listed.kill the one a the bottom and then it will play the dvd.
It took a while to figure this out but it looks like the sound system is trying to open a second player as both artsd and kaffeine both duplicate.
Am still looking for the reason why though.
The above works so at least i can watch a vid (had to do it twice a couple of times though)
On a side note i have no problems with dvds transferred to disk or tv but still have same problem on home made dvds
am also running edgy but have upgraded kde to 3.5.6 as i thought it may be a kde prob.

Edit 32bit edgy eft

---

### Post by kenmiles on 2007-04-03
I had this problem and found that if I changed audio to oss it cured the problem.
Regards, Kennneth.

---

### Post by sparky64 on 2007-04-04
Tried that and still have the same problem.
Or it says unable to load drivers.
Managed to get to play once using mplayer plugin, But had only  sound not 5.1 surround.

---

