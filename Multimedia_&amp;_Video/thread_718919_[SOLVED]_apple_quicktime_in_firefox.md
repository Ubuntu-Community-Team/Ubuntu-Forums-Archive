---
title: "[SOLVED] apple quicktime in firefox?"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by StOoZ on 2008-03-08
anytime I try to watch a quicktime trailer (apple's site), Instead of seeing the movie, its just show "no video" ..
any idea?

---

### Post by MattBD on 2008-03-08
As far as I know there is no Quicktime plugin for Linux. However, you could try installing MPlayer (sudo apt-get install mplayer) and this will include the mozilla-mplayer plugin, which might let you watch it. I'm not sure this will work, but it's certainly worth a try.

---

### Post by MattBD on 2008-03-08
Actually I just finished my previous post when I found [this blog article about running Quicktime under Wine]("http://wine-review.blogspot.com/2007/08/quicktime-716-on-linux-with-wine.html"). So if it doesn't work with MPlayer you could give that a try.

---

### Post by 6205 on 2008-03-08
With latest, updated Fluendo plugins is QuickTime playback flawless. But they are not for free...but anyway i don't use anything else anymore :)

[http://ubuntuforums.org/showthread.php?t=639393](http://ubuntuforums.org/showthread.php?t=639393)

---

### Post by justsomedude on 2008-03-08
mozilla-mplayer plays the trailers from Apple's movie trailer site without any problems.

Different plugins can block each other, so I suggest uninstalling totem-mozilla or the vlc plugin for mozilla if present.

Also cleaning out /usr/lib/mozilla/plugins can be necessary (if vlc and totem plugin are still present after uninstalling). 

Happy watching!

---

### Post by StOoZ on 2008-03-09
> **justsomedude said:**
> mozilla-mplayer plays the trailers from Apple's movie trailer site without any problems.

Different plugins can block each other, so I suggest uninstalling totem-mozilla or the vlc plugin for mozilla if present.

Also cleaning out /usr/lib/mozilla/plugins can be necessary (if vlc and totem plugin are still present after uninstalling). 

Happy watching!

thats solved my problem!! 
thanks a lot.
thank you all !!! :guitar:

---

### Post by Zash on 2008-06-19
Apples trailer-page specifically checks if one has QuickTime installed. I Got it to [work with this]("https://zash.se/bajs/apple.user.js") [Greasemonkey]("https://addons.mozilla.org/en-US/firefox/addon/748")-script.

---

### Post by saumoon on 2008-07-01
Greasemonkey with that scripts works perfectly !!
Nice Job !!

---

