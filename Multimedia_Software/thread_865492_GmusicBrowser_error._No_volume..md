---
title: "GmusicBrowser error. No volume."
date: 2008-07-20
forum: Multimedia Software
---

### Post by User3k on 2008-07-20
GmusicBrowser error

> Can't set the volume. That's probably because amixer {packaged in alsa-utils} is not installed.

I have a Nvidia HD sound card, the sound works fine with everything else.

These are installed,
alsamixer
alsa-utils
gnome-alsamixer

I also have xfce4-mixer installed.

Anyone know why I can't set the volume in GmusicBrowser, or have any guesses?

---

### Post by flytripper on 2008-07-20
try going into settings and changing the driver/mixer from in there.. you can .

---

### Post by User3k on 2008-07-20
In the GmusicBrowser settings the audio is grayed out. Except for mplayer and Icecast server (Plus I can check and uncheck the "Ignore playback error" box.

---

### Post by flytripper on 2008-07-20
so you cant change the output device?

---

### Post by User3k on 2008-07-20
Got it. The Icecast server was checked and I checked the mplayer one instead. Now it works. That was easy, lol.


Thanks for sending me back there again. I missed that the first two times I opened it.


Edit: What confused me a bit was the error I was getting. It had nothing to do with alsa at all.

---

### Post by keyshawn on 2008-12-04
I had the same problem that user3k described. 

However, my audio config in gmusicbrowser was already set on mplayer. 
I fixed it by opening mplayer's 'advanced options' (within gmusicbrowser) and toggling the 'amixer control' to master.

---

