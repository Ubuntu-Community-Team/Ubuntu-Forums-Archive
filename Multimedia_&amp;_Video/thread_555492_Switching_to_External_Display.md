---
title: "Switching to External Display"
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by abish on 2007-09-20
hello.
i started using ubuntu 7.04 recently.
How do i connect to the external monitor?
it worked fine when i was using windows in my laptop (HP Compaq 3425 AU, NVIDIA)
Fn+F4 doesnt work.
please help me out.:(

---

### Post by abish on 2007-09-20
well, now i can use the external display.. but the only problem is that to toggle.. i need to restart... !
is there any simple solution?
the function+f4 doesnt work!

---

### Post by d1ss0nant on 2007-11-15
Hi there - i also have this issue.  In the beginning, I was forced to physically restart like you...my solution is not a good one - fn+f4 still doesnt work, but at least I dont restart fully?  See what you think of this:

i do cntrl+alt+f1 to open a fullscreen terminal - this will display on both monitors (laptop and external)

I run "ps -e" to see all my current processes (and their corresponding PIDs)

I use shift+pg up to find the XORG pid

I type "Kill xxxx"  (where xxxx is xorg's PID)

I am logged off, the display comes up on the external monitor in full GUI mode, and i log in like normal.

like I said, not really that great of a fix, but it beats restarting!  Let me know how it works for you

---

