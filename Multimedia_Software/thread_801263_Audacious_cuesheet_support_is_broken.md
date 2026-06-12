---
title: "Audacious cuesheet support is broken"
date: 2008-05-20
forum: Multimedia Software
---

### Post by Artemis3 on 2008-05-20
Audacious cuesheet support is broken in the Hardy release.

There is a workaround: In preferences -> audio disable "detect file formats by extension", then add each .cue to the playlist.
To play the songs, you have to go back to preferences -> audio and enable "detect file formats by extension".

Tested with tta+cue files.


Has anyone found another solution?


[Related to bug 204933](https://bugs.launchpad.net/ubuntu/+source/audacious/+bug/204933)

---

### Post by 2ig2ag on 2008-06-19
Solution in ubuntu 8.04:
1.get audacious-plugins-extra1.5.0 package
2.Go to 'Preferences - Plugins - Decoders' and check 'Cuesheet Plugin' in audacious 1.5.0
3.Go to 'Preferences - Audio' and uncheck 'Detect file formats by extension' in audacious 1.5.0

---

### Post by remicks916 on 2008-08-07
Not working for me, hangs audacious and crashes :(

---

### Post by Major_Kong on 2008-09-03
Same here, only 'worked' once (didn't play).

---

