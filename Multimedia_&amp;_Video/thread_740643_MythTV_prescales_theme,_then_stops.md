---
title: "MythTV prescales theme, then stops"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by Mohonri on 2008-03-31
I have a newly setup MythTV box.  It is running Gutsy, with a frontend and backend on the same machine.  I got it all running according to the guides here.  When I first set everything up, I noticed that occasionally, the frontend would start up, prescale the theme images, and then just stop with no menu at all.  This didn't happen consistently, and usually if I quit and restarted the front end, it worked again.

Since that time, I have made two changes:  1) I modified xorg.conf to get an output to my TV (which works just fine) from my GeForce 6200, and 2) I set up lirc.  Now, I can't get the frontend to get to the menu at all.  Restarting the frontend and even rebooting doesn't seem to have any effect.  If I hit Esc, I get the "Do you really want to exit?" dialog, which works as expected.  (BTW, selecting "no", which would take me back to the main menu, just takes me back to the blue background).

Does anyone have any suggestions on what I'm doing wrong, or how to debug it?

EDIT:  Well, it must be some sort of overlay thing with the nVidia card.  You see, I'm configuring it from another box through vnc, and when I turned on the TV just now, the menu appears just as it should.  I have the TV setup as TwinView.  Is there a way to get the menu to show up on both screens?

---

