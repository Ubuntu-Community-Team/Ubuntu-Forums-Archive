---
title: "Nvidia artifacts after mythfrontend crashes"
date: 2011-03-01
forum: Mythbuntu
---

### Post by romanyiv on 2011-03-01
Got to be a common issue with Mythbuntu 10.10 and .24.   Mythtv looks fine - HD works great - even with 1080p content.  But if mythfrontend crashes - which occurs sometime - I have "snowy" kind of artifact that remain.  It's like some garbage got left in video memory.   Restarting mythfrontend does not eliminate it - some of still "bleeds" thru depending on the video content.  Rebooting solves it until the next time.   Have the same thing occur on another mythfrontend client.   Any suggestions?  Not a big problem - I've lived with it for a few months now - but annoying...

---

### Post by kokkonenfi on 2011-03-02
I have the same issue with 2 different Ion frontends. Now days I just try to avoid crashing, I have to reboot to get rid of the artifacts.

---

### Post by larsolav on 2011-03-02
Ditto here!
(sorry, not much help, I know. At least you know you are not alone...)

---

### Post by lviperz on 2011-03-03
I'll join the party. I get the same artifacts when the frontend crashes.

---

### Post by uncle hammy on 2011-03-03
This is a known issue with the > 256 nVidia drivers.  The only real solution is to downgrade to the 256 drivers.  Though I will tell you I downgraded to the 256 drivers, and my machine completely locks if the frontend crashes so I had to go all the way to the 195 drivers.  I am now running the 270 drivers, and although this problem still exists, my frontend crashes are so rare, I can live with it.

[http://www.gossamer-threads.com/lists/mythtv/users/467324?search_string=the%20problem%20260%20drivers;#467324](http://www.gossamer-threads.com/lists/mythtv/users/467324?search_string=the%20problem%20260%20drivers;#467324)

I suppose you could always rig a remote key to restart X (sudo service gdm restart) which will get you the same results as a full reboot.

---

### Post by romanyiv on 2011-03-06
Knowing that I'm not the only one is a big help.  Like I said it's not a big issue - just an annoyance....

---

