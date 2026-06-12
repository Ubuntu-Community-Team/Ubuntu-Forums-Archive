---
title: "GeForce 5500"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by the fish on 2007-06-07
i have try everything that i have found on here.  no one else has the same problem from what i have found. 
so here it is i plug in my video card and then my computer won't boot. i am out of options. please help.  the video card does work i had in a friend computer to test it.

---

### Post by dannystaple on 2007-06-07
Hi there,
Is this a new card or an old one?
When you say "does not boot" - does it get beyond post (the BIOS Power On Self Test screens) or is the monitor just never activated? Or does it get part of the way into Ubuntu and then die?
I am not sure how much it will help, but how about posting your machine specs - motherboard, CPU, and then see what that might indicate.
Cheers,
Danny

---

### Post by topsites on 2007-06-07
Have you tried Envy?

I think in your case, you'll be looking for the newest driver (literally, nvidia-glx-new) but don't quote me, there's a list floating around somewhere that has all the cards and their models listed by driver... My geforce4 takes the 9631 version, (literally, nvidia-glx) and older cards take the legacy driver (nividia-glx-legacy).

It is a matter of first finding the correct driver, then completely uninstalling whatever driver you currently have, re-installing the right driver, configuring the x server, omg man I spent weeks dealing with it but I did get it working and so have most other folks, patience and perseverance pays off.

---

