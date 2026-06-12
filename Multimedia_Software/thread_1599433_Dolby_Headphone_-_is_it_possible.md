---
title: "Dolby Headphone - is it possible?"
date: 2010-10-17
forum: Multimedia Software
---

### Post by blacktrance on 2010-10-17
Recently installed Ubuntu, everything works well. But there's one thing missing that I liked in Windows. I had Dolby Headphone in my audio driver, and it significantly improved listening. Is there something like that for Linux? If so, how do I use it?

---

### Post by waveman77 on 2011-02-21
> Recently installed Ubuntu, everything works well. But there's one thing  missing that I liked in Windows. I had Dolby Headphone in my audio  driver, and it significantly improved listening. Is there something like  that for Linux? If so, how do I use it?

As far as I have been able to determine, no Linux players support Dolby Headphone as such. There are alternatives though.

Some players support bs2b ([http://bs2b.sourceforge.net/](http://bs2b.sourceforge.net/)). Eg Audacious supports it via preferences/plugins/effects/LADSPA Host. This works pretty well for me.

Amarok has no support at the moment.

Sox has 'earwax' support which does a similar thing.

VLC has its own "spatializer" but it tended to fall apart and generate large amounts of noise and/or not do anything, while using lots of CPU when I tried it. It also lacks documentation - it's unclear what the options mean. It seems to not even turn on at all in the current source tree.

I've been talking to Amarok people about adding bs2b support to it. They seem to think it should be done in Phonon backend but there does not seem to be an obvious place in Phonon to put such a module. More discussion when the phonon people get onto IRC.

Some people have worked out how to use the Dolby Headphone dll file (DOLBYHPH.DLL) in plugins eg the foobar plugin and there is one for another software that I forget. YOu may be able to get the Dolby DLL from some products like some windows DVD players.

Hope this helps.

Tim

---

### Post by aeiah on 2011-02-21
looks like this guy got the plugin working with alsa system-wide:
[http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html](http://www.rpgameplace.de/blog/index.php?/archives/21-Stereo-to-binaural-with-ALSA-using-bs2b-LADSPA-plug-in.html)

article is quite old, but then so is this post :p

---

