---
title: "SOLVED: Flash in Opera!"
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by maximilion on 2008-02-12
I started with Firefox right after a fresh install. (Ubuntu 7.10, 32-bit)

After apt-getting flashplugin-nonfree and failing, I tried Gnash. Didn't work either.

OK, started Opera, followed the procedure on Opera.com's Linux install page. Didn't work. Read some old thread from 2005 in these archive suggesting Opera need Motif. Found it wasn't so; still didn't work.

Went back to Firefox. Removed previous Flash plugins Completely via Synaptic. Got a flashplugin-nonfree 9.0.115.0. It worked!

Then I went back to make it work in Opera (latest stable, v9.25). It didn't, even though Opera looks in Firefox's plugin folder. (/usr/lib/firefox/plugins on my machine, "locate flashplugin-" to find all installed flash plugins. 

When I tried installing it in Opera before (see above), of course it put another plugin in Opera's plugin folder. So since Opera looks in Firefox's folder, two plugins were loaded. Removed the one in Opera's plugin folder.

Still didn't work. Went to Opera Forums, and lo and behold: Support said latest Flash version supported in 9.25 is Flash 9.0.48.x, but latest beta (Opera 9.50b) supports latest Flash, 9.0.115.0!


Downloaded it, installed it, and everything just worked.

Summary: Opera might be easier to get going with Flash than Firefox! I wouldn't be surprised at all, if it's just a matter of downloading Opera 9.50b! (Only if the Flash in Synaptic doesn't work, you could [get Flash 9.0.115.0]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&promoid=BONRN") from Adobe and overwrite the Synaptic one I guess.


I would be very interested in finding out if this is true. Have you gotten flashplugin-nonfree from Synaptic, but Flash refuses to work in Firefox? Then please download [Opera 9.50b]("http://www.opera.com/download/?ver=9.50b") and try if Opera just works right away :)

---

