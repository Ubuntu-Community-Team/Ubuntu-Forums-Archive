---
title: "another ps3 mediatomb thread"
date: 2008-08-10
forum: Multimedia Software
---

### Post by dogsipod on 2008-08-10
last week I installed mediatomb on my ubuntu hardy 64bit amd install.  i followed the one of the numerous guides about how to go in and comment in the right lines in the config files to enable ps3 support. after a few minutes of configing it worked perfect on my ps3. i was watching episodes of the venture bros and listening to all my music.  i didn't mess with it much during the week but today i wanted to listen to some music on my home theater system after.  i started up mediatomb on my linux box turned on the ps3 and nothing.  no servers where listed. i tried restarting both and searching for media servers via ps3 and still nothing.  i reinstalled mediatomb following same guide i use before and nothing.  before when it worked i went into the ps3 browser and went to the [http://address:port](http://address:port) used to access the mediatomb UI. but now when i try this on the ps3 or any other computer on my home network (besides the linuxbox) it just times out.  any idea on why all of a sudden mediatomb stopped serving?

---

### Post by dogsipod on 2008-08-10
nvm.  i solved the problem.  I was using a firewall earlier in the week and though i removed it, it left behind the files that closed the ports on my linux box. i deleted the files and now mediatomb and ssh work again.

---

