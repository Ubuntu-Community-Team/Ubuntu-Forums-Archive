---
title: "[SOLVED] Has VLC lost its post-processing ability?"
date: 2009-01-07
forum: Multimedia Software
---

### Post by Open-SuSe-A-Me on 2009-01-07
The first time i had used a VLC above 0.8.6X the right-click option to enable post-processing was not there, and nowhere to be found.  Then when i got it on Windows, it was also missing.  Whats going on???

One more reason why Hardy > Intrepid.

---

### Post by Drubie on 2009-01-07
> **Open-SuSe-A-Me said:**
> the right-click option to enable post-processing was not there, and nowhere to be found.

What? That sucks!

by golly, it is gone!  lame...

---

### Post by Open-SuSe-A-Me on 2009-01-07
I dont see any reason they would remove this feature.  Anyone know why/what happened?

---

### Post by Supersaiyan.IV on 2009-01-07
VLC &#8594; Properties &#8594; Video &#8594; Filter &#8594; Video Postrprocessing Filter

Gone, because it's enabled by default, and most likely disabled automatically during playback of HD content.

---

### Post by Open-SuSe-A-Me on 2009-01-07
Ahhh I see now, thanks.  But that's completely rediculous that i have to go that deep into the configuration just to change it.  And having it on by default is a terrible idea.  If you process a file that doesn't need it it gets a weird "blinking" effect.

And why would they decide it was a good idea to make the video play in its own separate window like Mplayer?

---

### Post by mc4man on 2009-01-07
> And why would they decide it was a good idea to make the video play in its own separate window like Mplayer

What version of vlc 0.9.x are you using?

By default the source code has the 'embedded' video disabled, videolan considers it broken. It can easily be re-enabled before compiling.

Intrepid is using the 0.9.4 version with 'embedded' enabled, the korn launchpad ppa has a 0.9.8a deb with embedded for hardy.

---

