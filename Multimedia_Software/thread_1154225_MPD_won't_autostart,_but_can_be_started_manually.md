---
title: "MPD won't autostart, but can be started manually"
date: 2009-05-09
forum: Multimedia Software
---

### Post by mikezila on 2009-05-09
[COLOR=Green]**SOLVED, check post 3.**
[/COLOR]
I use, and love, MPD.  I think it's perfect.  The only problem I have is that doesn't start when the system boots.  If I log in, and do "sudo /etc/init.d/mpd start" it start with no errors or fuss, but at system boot it just doesn't happen.  I also don't seem to have any into about this silent failure anywhere in my logs, though it's possible I'm just checking the wrong ones.

Is there any way I can sort of "set a trap", so I can't watch it try to start, and see why it's failing?  Or indeed, find out why it's not even being started, if that is the case?

---

### Post by mikezila on 2009-05-09
Well now I can see that's it's failing because it can't bind to port 6600, which is for some reason something it doesn't have trouble with once the system is up and running.

Does anyone else have any clue?

---

### Post by mikezila on 2009-05-09
It seems I'm dedicated to making things more complicated than they need to be.  I was (for some reason) trying to bind the mpd daemon to a specific address, and that address wasn't available at the time mpd was starting up, but once the system was started and settled, it was, which is what made it fail at boot, but succeed once I was logged in.

Fixed by commenting out (or deleting) the "bind_to_address" line in mpd.conf

---

