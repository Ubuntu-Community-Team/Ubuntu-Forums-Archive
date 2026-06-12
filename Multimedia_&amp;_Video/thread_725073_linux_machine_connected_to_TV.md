---
title: "linux machine connected to TV"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by aknight_sa on 2008-03-15
good day guys,

i have an extra PC at home which i have connected to my TV via S-video cable.. i want to use this machine for watching movies.. the problem is everything goes blank when linux boots... my xorg.conf doesnt have any display option for the TV

the card i have is the ATI X1950 pro

thanks

---

### Post by jimmy the saint on 2008-03-15
check out "atitvout".  It's a simple little program that fixed the issue for me.  The only downside is that it doesn't have a gui.  That said, if you will be only using the box to watch movies, it should work for you.
If the standard command doesn't work, just try a few of the options.  It took me about five minutes to figure out the right command/option combo for my card, but once I did, everything worked like a charm!

---

