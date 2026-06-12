---
title: "Weird VLC Issue - Movie Viewing Area isTransparent ???"
date: 2009-10-04
forum: Multimedia Software
---

### Post by bluelamp999 on 2009-10-04
Hi All,

I'm running VLC 1.0.2 on (a relatively fresh) Jaunty install.

A lot of the time when I try to watch a video clip (usually an AVI), VLC will appear to play the clip but the movie viewing area is transparent (see attachment, that's my desktop in the background).

The audio is fine and a restart cures the issue (for a while!)

Has anybody else experienced this?

Any ideas how to address this issue?

Thanks!

---

### Post by justsomedude on 2009-10-04
1. Try to disable desktop effects.

2. If that doesn't help (or even if it does, we want fancy eye candy, right?), go to Tools --> Preferences --> Video --> Output in VLC and see if other output modules work. You have to save and restart VLC every time you try a new output module.

Could also be related to the video driver, if it happens only after a while, it could be some kind of buffer issue...

---

### Post by bluelamp999 on 2009-10-04
Thank you dude!

Changing the output module to 'OpenGL video output' allows me to at least watch the video, though I can't do stuff with the app menus as the video immediately overwrites the menu. 

But this is a *vast* improvement over transparency, right?

As for desktop effects, I wish...

I'm lumbered with an ATI Mobility X300, no longer supported by the newer Catalyst drivers *and* I'm also dual monitor.

Roll on decent FOSS ATI drivers...

Thanks again...

---

### Post by justsomedude on 2009-10-04
Well, I'm glad it works at least somehow.

I've got (almost) no experience with ATI cards, so I can't help you there, but you could uncheck Tools --> Preferences --> Interface --> Embed video in interface. 
This way, you should at least be able to use the menus.

Good luck.

---

### Post by bluelamp999 on 2009-10-04
Fantastic!

Dude, you're a VLC guru!

Cheers

---

