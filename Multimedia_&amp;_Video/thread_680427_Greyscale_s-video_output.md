---
title: "Greyscale s-video output"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by HaDAk on 2008-01-27
I've recently gotten my Mythtv box up and running. I was happily watching TV, and mythfrontend locked up.  I rebooted my machine, and when it came back up, it was in greyscale.  It's not an issue with my xorg.conf file, because it's greyscale during post and during the bootsplash.

I'm using a Geforce 6600AGP with s-video output to an RF modulator (NTSC).  I've been searching the internet for hours, and I'm very frustrated.  Does anyone have a hint? Solution? ...something?

Thanks :-\

---

### Post by yabbadabbadont on 2008-01-27
Strangely enough, I've seen this with loose cable connections.  Maybe it was just a coincidence that it happened after the lockup?  Try re-seating all the cables and see if it helps.  (It can't hurt, and doesn't take long to try)

---

### Post by HaDAk on 2008-01-28
I tried reseating the cables.  I thought there might also be a problem with the rf modulator detection on startup, so I unplugged the cable until after the system posted.  It didn't give video for the rest of the boot time, until the drivers initialized the output.  (That's the way it was starting up when it had color, thus leading me to believe that might help.)  After ubuntu started, it was still greyscale.  I reseated the svideo cable yet again, to no avail.  This isn't the first time i've seen this. In fact, I've seen it several times before.  I have svideo in on another TV, and I get the same greyscale output.  I'm tearing my hair out here. I have no idea what is causing this, or how to fix it. I only know that I keep seeing it, and I feel helpless against it.

---

### Post by HaDAk on 2008-01-30
Alright, I seem to have figured out the issue. Kinda. At least, I found a solution. I think. :)

I added, to my xorg.conf file, under the Video card device section, these two lines:
Option "TVStandard" "NTSC-M"
Option "TVOutFormat" "SVIDEO"

Restarted X, and it came up in color.  I'm not sure what caused the problem, but at least it's in color...at least until I reboot? I'm too afraid to try. ^^

---

