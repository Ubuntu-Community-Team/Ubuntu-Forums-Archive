---
title: "Resolution suddenly gone?"
date: 2009-02-27
forum: Multimedia Software
---

### Post by Fafnr on 2009-02-27
Hey,

I had a projector hooked up to my laptop running ubuntu 8.10.
To do that I had to change the resolution.

However, now it's as if Ubuntu doesn't recognize I've removed the projector? I usually run 1600 x 1050 (or something like that - strange Dell form-factor screen... :), but suddenly I can only choose a max of 1360 x 768? And I can select an "unknown" screen - but none are attached other than the main screen.

I've tried rebooting, etc.

I've tried doing "detect displays", but that doesn't help either...

Any ideas?

Thx!

Søren

---

### Post by bongomachine on 2009-03-13
I have the same problem!!

---

### Post by tgyorgyi on 2009-05-04
Hi, I had this too, both, with a projector and with an external LCD display which favors other screen resolutions than the default of my laptop. 

Please check if there is a new subsection in your /etc/X11/xorg.conf file, which contains the words "screen resolution" and then a number for the resolution of the projector. If yes, comment out (just to be on the safe side) the lines for this section from "subsection" to "endsubsection", and then sign out and back again. Now you should have the right resolution OR if you go to Settings/Screen, you should have the corrent resolution in the list available again.

---

