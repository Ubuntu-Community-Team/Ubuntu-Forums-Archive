---
title: "Can somebody confirm that these mplayer commands are correct?"
date: 2011-02-21
forum: Multimedia Software
---

### Post by Mojo McCracken on 2011-02-21
Here's the thing: I only have one speaker. Monophonic output is required.

So, I did a little research and found this little wonder (under *2.3.2.3.7 Panning filter*): [http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/sound.html](http://web.njit.edu/all_topics/Prog_Lang_Docs/html/mplayer/sound.html)

So, apparently my hero is *mplayer* and the command is:

```
mplayer -af pan=1:0.5:0.5 -channels 1 [radio stream.pls]
```

For streams in .m3u format a *-playlist* option is required (apparently). The code is thus:

```
mplayer -af pan=1:0.5:0.5 -channels 1 -playlist [radio stream.m3u]
```

Really, the only thing I need to know is whether or not this is actually correct. The commands work, but there's really no way for me to test if the streams are actually downmixed. I've tested the *-af pan=1:0.5:0.5 -channels 1* command on an .mp3 stereotest (with succes), but then it hit me: Is it even possible to downmix live streams on the go?

All help, additions and suggestions are greatly appreciated!

---

