---
title: "DVD Playback problems"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by lwatcdr on 2008-03-10
When I try and play back a DVD it sort of works. The video is all blocky and the audio breaks up. I have tried it with both VLC and with Mplayer. with the same results.
I am running the latest stable version of Ubuntu on an Athlon X2-64 in 32 bit mode. 
My video card is an Nvidia 6600GT and I am using the restricted drivers.
Any ideas?

---

### Post by ve3rpm on 2008-03-16
I started out with the same issues and then found this post... worked for me although I'm running 64 bit.  The instructions are for both though.  Hope it helps
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by mvan83 on 2008-03-21
I had a similar problem. Not sure how "bad" your picture looks. When I was playing dvd's, they would have annoying horizontal lines. The playback was not smooth at all. I'm sure my system was not lagging due to hardware. This was not with a lot of things running. After fiddling around with a few things, I tried switching from the restricted "nvidia" drivers back to the "nv" (generic) drivers (btw, the gui did not let me change this, and then at one point it forced my resolution down and wouldn't give me the option of increasing it to full capacity of my monitor -- I had to edit the driver in my xorg.conf file -- be sure to make a backup if you edit this way). Voila, my dvd playback is now as smooth as can be. No more horizontal lines. Of course, now my desktop effects can't be enabled and mythtv doesn't appear to start either :( Really seems quite silly that this is what I have to do to get smooth dvd playback. Any other videos I played, including HD, and also HD tv through mythtv were as smooth as could be (with the restricted drivers). But dvd playback was poor. It would be nice to find a solution that didn't involve what is effectively a major downgrade. Hopefully with Hardy, the drivers (or configuration, or whatever it is) will be fixed for dvd playback.

---

