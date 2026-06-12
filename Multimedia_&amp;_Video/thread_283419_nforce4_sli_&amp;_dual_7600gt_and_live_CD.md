---
title: "nforce4 sli &amp; dual 7600gt and live CD"
date: 2006-10-24
forum: Multimedia &amp; Video
---

### Post by Totzo on 2006-10-24
I'm wondering if this is just me or there are others with a similar problem.
I have an nforce4 motherboard with 2 7600gt graphics cards set up in sli mode. As I type I'm using edgy with the beta drivers and sli working.

The card that is connected to my monitor is peg1 and set up as the primary card in my bios.

Here is the problem, when I try to run ubuntu (dapper or edgy) from the live cd, the wrong card is detected and I end up with a black screen. I then have to edit my xorg file so that it uses the right one- a bit of a pain really.

While this isn't a total show stopper for me it might be for a someone who hasn't used linux before. 

Maybe there should be something in place for card selection on the live cd boot process before X is started?

---

### Post by thexaspect on 2006-11-25
Have you made sure the nforce onboard video is disabled in the bios? If you're loading an OS, it's always looks for the easiest route to installation, and trying to load dual 7600 gt's in sli mode on boot is definately not the easiest way. worst case, plug your monitor into the onboard, and install, and reconfigure vdieo when you're done, that what i had to do with mine. i've got an a8n-sli with dual 7600gt's also =) and so you dont bang your head against the wall like i was, to un dual monitors, you cant use sli. either just run the cards parallel, or use one monitor on your sli cards, and the other into your onboard video or another card. cheers =)

---

