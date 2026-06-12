---
title: "may i disable XvMC for dvd playback via internal player?"
date: 2007-10-14
forum: Mythbuntu
---

### Post by stevetv on 2007-10-14
as a reference, ive included this gossamer thread.

[http://www.gossamer-threads.com/lists/mythtv/users/294486?search_string=XvMC%20dvd;#294486](http://www.gossamer-threads.com/lists/mythtv/users/294486?search_string=XvMC%20dvd;#294486)

i use XvMC for tv playback (which is SD digital).  i find it gives me better picture for fast moving situations - like sport.

but i need to disable it for dvds.  else i get slow video playback and crap sound making it unwatchable.

i think this problem also was discussed in ticket #3125.  but maybe this is a slightly different problem.

i can obviously change my dvd player to xine - which will probably fix the problem.  but i'll need to remap my remote for this.  i can also jsut change codecs when i want to watch dvd's .. but the GF won't like this.

does this issue affect anyone else?  maybe im the only one that uses xvmc... probably am.  

can i make a hack that will change the mpeg codec from standard xvmc to ffmpeg when playing dvds?  The solution on the mythtv wiki, that turns off xvmc for everything except HD isn't helpful to me as my broadcasts is 720x576.  i want to use xvmc for everything except dvd's (and anything else that i find in the future that doesnt work).

thanks.

---

### Post by superm1 on 2007-10-14
Personally, i'd say just go xine for now.  As described in that thread on -users, there aren't many ways to work around this with -fixes.  Come the release of 0.21, consider going back to internal for the player.

---

### Post by laga on 2007-10-14
> **stevetv said:**
> 
i can obviously change my dvd player to xine - which will probably fix the problem.  but i'll need to remap my remote for this.  i can also jsut change codecs when i want to watch dvd's .. but the GF won't like this.



mythbuntu-lirc-generator should have set up xine to work with your remote automagically. If it didn't, file a bug ;) [https://bugs.launchpad.net/mythbuntu/](https://bugs.launchpad.net/mythbuntu/)

---

