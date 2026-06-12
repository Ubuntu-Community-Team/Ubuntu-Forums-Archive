---
title: "Exile and Rhythmbox won't play songs..."
date: 2008-09-21
forum: Multimedia Software
---

### Post by eudemonis on 2008-09-21
I've had Ubuntu for a month... Installed Exile and rhythmbox to play my music. They worked fine but recently both of them won't play any songs. I press play and there is no response from either player... any ideas? (yes, the volume is up).  Simply, both programs won't play any songs... the play icon goes on but songs don't begin...[HTML][/HTML]

---

### Post by Crafty Kisses on 2008-09-21
Try running the programs in the Terminal and see if you get any errors.

---

### Post by eudemonis on 2008-09-21
pardon my ignorance but how do I do this? :) I know how to open terminal window and run some things but how do I play these programs in terminal I'm not sure... thanks for your help

---

### Post by eudemonis on 2008-09-21
yeah, I run them from the terminal window they just open no problem.  I'm sure it's something stupid but I can't think what it is...

---

### Post by soxs on 2008-09-21
for exaile to play a track from some location on your hard disk:
```
 exaile "/path/to/track/track.extension"
```
or you can simply resume playing from the last time you started exaile via: ```
exaile -a
```

I dislike rhythmbox, so you either will have t you read ```
rhythmbox --help
``` and/or ```
man rhythmbox
``` or stick to the much "better" exaile (whcih is written in smoooothh python :-P )

---

### Post by eudemonis on 2008-09-21
this is the message I get: what does it mean?

ReplayGain support requires gstreamer-plugins-bad 0.10.5
Fetching available plugin list

---

### Post by soxs on 2008-09-22
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse 
```

This should fix your issue.

To extinguish any gstreamer related media-format errors do:
```
sudo apt-get install gstreamer0.10-plugins-bad  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-good gstreamer0.10-ffmpeg gstreamer0.10-fluendo* gstreamer0.10-schroedinger gstreamer0.10-pulseaudio gstreamer0.10-sdl
```

---

### Post by DanPiazza on 2008-11-12
I am having this same problem. The sudo didn't fix it. I'm also new to Ubuntu, so troubleshooting is at a minimum.

---

