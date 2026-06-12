---
title: "firefox crashes on flash with sound"
date: 2006-12-05
forum: Multimedia &amp; Video
---

### Post by eilu on 2006-12-05
For some reason, Firefox 1.5.0.8 on Dapper crashes whenever I view a page that has flash with sound, regardless of whether the sound plays or not. Flash without sound doesn't trigger the problem, just those with sound.

I isolated the casue because one of my guilty pleasures is playing Neopets. Firefox does fine when I navigate across most of the site (flash-based maps, comics) but crashes when I load a game (which has sound) or view the advent calendar (a seasonal feature, which also has sounds) :( 

On one of the advent calendar flash animations (with sound effects) the page laoded the animation, but there was no sound, then the whole thing stopped responding when I tried to navigate away from the site, I had to force quit and restart.

I'm thinking it's a Firefox/Ubuntu problem because things are ok on the windows boot, my system can play the flash files sound & all (it just takes awhile to laod on dial-up)

In case anyone needs to know: I'm using flash 7 (or whichever it is that came with firefox; I'm pretty sure it's 7 because it isn't 9 and 8 doesn't exist for linux)

Any ideas?

---

### Post by Shatrat on 2006-12-05
You can check for sure what flash version you have here,
[http://www.adobe.com/products/flash/about/](http://www.adobe.com/products/flash/about/)

One known problem with audio is that in /etc/firefox/firefoxrc there should be a setting which says FIREFOX_DSP="none"

Other than that, I'm not sure how to improve the reliability of flash. I still have problems with it crashing occaisionally as well.

---

### Post by eilu on 2006-12-05
about:plugins says 

```
Shockwave Flash
File name: libflashplayer.so
Shockwave Flash 7.0 r68
MIME type: application/x-shockwave-flash (Shockwave Flash); application/futuresplash (FutureSplash player)
```

and yes, there is a FIREFOX_DSP="none" setting.

---

### Post by drphilngood on 2006-12-05
You could use [NoScript]("https://addons.mozilla.org/firefox/722/") as a temporary solution to let you view the pages without crashing until you find a real fix.

---

### Post by tehdon on 2006-12-05
There is a flash 9 that is still in beta (i think beta 2 at the moment)
out of my own about : plugins

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 d78

-
I got that one out of the multiverse or universe repository (I think, I have them all enabled) performed a manual 'sudo apt-get update && sudo apt-get upgrade' one day and it was in the ugrade packages.  I have had MUCH better luck with this version actually functioning properly.  Occasional audio glitches, but no more Firefox lockups, unexpected error quits, or hung video/audio.

---

### Post by eilu on 2006-12-08
Worked for me too, though it took forever to download. Thanks!

---

