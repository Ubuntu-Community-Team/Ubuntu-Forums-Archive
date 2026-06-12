---
title: "Resolution problems in MythTV"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by jba6511 on 2007-05-28
I downloaded and configured mythtv and then changed the resolution settings to something like 572x400. I uninstalled mythtv via synaptic and then reinstalled. Once I reinstalled the problem was still there, the giant resolution. I do not know how to change the resolution since I can only see part of the screen (like the GEN from general) and can not make it through all of the options. Is there a way to completely remove mythtv, including the config files so that when I reinstall it is in the native resolution? or change the resolution of mythtv without opening the configuring it in the back end?

---

### Post by frokki on 2008-03-15
I updated my MythTV from 0.20 to 0.21 and got this same problem. If I open frontend on my 2nd display, a TV, I can only see the upper left corner of mythtv, but at least I can close it. But if I open it on my default screen, despite closing it the screen resolution stays somehthing like 450x300 and I have to reboot my machine to get it back right. 

I've tried purging and reinstalling all mythtv packages, but with no luck. Could someone help me please?

---

### Post by frokki on 2008-03-18
SOLVED!

I sent a private message to the original poster, but he couldn't remember how he solved the problem. He suggested trying dpkg to reconfigure mythtv, but unfortunately there wasn't any screen resolution options in those configuration wizards.

So I decided to blindly mess up with the appearance settings, and after 10 minutes of random smashing I got it running in a window and was able to choose the right settings :D 

Note-to-self: Always double-check that the programs adept wants to update aren't running!

---

