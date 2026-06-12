---
title: "monitor detection"
date: 2006-05-26
forum: Multimedia &amp; Video
---

### Post by sopo_dan on 2006-05-26
i was just thinking: shouldn't one be presented with an option to manually choose one's monitor make/model if it isn't autodetected during install?

sure, resolution can still be selected, but you end up with a 60Hz refresh rate and no option to set it higher, except manually editing xorg.conf. and even that isn't just about changing an entry from "60" to, let's say "100". you have to go generate a custom modeline, etc, etc

i know what monitor i'm using. why not let me select it. or at least let me select a refresh rate.


Edit: maybe this should have gone in the "development" forum. if anyone thinks so, i'm sorry and please move it.

---

### Post by chris_andrew on 2006-05-26
Have you tried 
[I]
dpkg-reconfigure xserver-xorg[/I]

Cheers,

Chris.

---

### Post by sopo_dan on 2006-05-26
hey, i'm not saying it can't be done. but wouldn't it be the easyest way to select it during install. i don't know how much trouble it would be to program that into the installer, since i have no clue about programming. but i don't think too much, seeing that most (important) distros have that.
and i'm making this point from the "new linux user" point of view (i'm wouldn't say i'm experienced myself, but not a complete noob either), who usually is a bit afraid of the command line or cfg file editing. and i think this is an important aspect of a "first contact" - having a pleasant viewing experience.

---

