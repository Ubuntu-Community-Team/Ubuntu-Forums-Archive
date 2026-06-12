---
title: "Updated, now won't boot"
date: 2009-11-25
forum: Mythbuntu
---

### Post by miststlkr on 2009-11-25
I had an install of Mythbuntu 9.10 running fine and last night I got a notice that there were updates.  Like a fool I downloaded them and now I can't boot.  I end up at a black screen with what I assume is a white terminal window that is too small to read.  I can get the boot menu thru GRUB and load *.15 [generic] just fine, but it does not recognize my onboard sound when I go this way.  It had been working fine previous to this batch of updates.  So is there a way that I can go in through the generic/restore version to find out what, exactly, was changed and perhaps even undo the updates??  I'd assume that is what the mode is for, no?



Thanks for helping out a noob.

---

### Post by byronmyth on 2009-11-25
When I accepted the 1.90 updates I found that it didn't recognise my TV, I had to plug a monitor into my video card (Nvidia Geforce 9600), it then saw both the monitor and TV and was fine after that point. Not sure if you are getting something similar?

---

### Post by miststlkr on 2009-11-25
I had a similar problem, but fixed it in the X config files by adding the second display manually.  After that the system ran great until I installed updates (from the downloaded install, not positive of the build offhand) and rebooted; it never came back.  I went to the boot menu in GRUB and have the option to boot as normal, boot *.15, "15 generic, .14, .14 generic, or memtest.  the generics will boot but no sound, the non-generic choices all pop up a very small terminal window with a "wait" mouse pointer which never goes away.  I can't read the writing in the term window but it LOOKS like it is the usual /home/USER/ dir, ls willclearly work though again I can't read the text due to resolution.

Is there perhaps a way to force the system to boot in --verbose so I can see where exactly it hangs?

Thanks for any suggestions!

---

