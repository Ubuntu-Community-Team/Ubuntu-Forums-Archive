---
title: "Mencoder audio delay"
date: 2009-02-03
forum: Multimedia Software
---

### Post by fatalGlory on 2009-02-03
Here's what I do:
[1] Rip a dvd to the hard drive like so:
```
mplayer -dvd-device /media/SOME_MOVIE -alang en dvd://1 -dumpstream -dumpfile /path/to/output.VOB
```

[2] Encode to XVid/MP# avi file:
```
mencoder -ovc xvid -xvidencopts bitrate=1024 -oac mp3lame -o /path/to/output.avi /path/to/output.VOB
```

When I'm done the resulting file plays fine in Totem, but in MPlayer the audio is about 500ms out of sync.  I can always just adjust the delay using the numpad +/- buttons after I open MPlayer, but it seems like it just shouldn't be this way.

It seems to only happen with some DVDs and not others though.  My most recent attempt that gave me the strange AV delay had a resulting VOB file that was 5.8Gb and I'm wondering if the large file size has any effect.  It also seems that in the encoding step, some files generate a large number of "Skipping frame!" lines near the start (I am wondering if this is what causes the desync).  I will have to test a few more DVDs i guess to see if there is a correlation.

Anybody else have these issues with mencoder/mplayer?

---

### Post by andrew.46 on 2009-02-03
Hi,

Something simple to try might be the filter 'harddup'. This would make your syntax:

```

$ mencoder -ovc xvid -xvidencopts bitrate=1024 -vf harddup \
-oac mp3lame -o output.avi input.VOB

```

One thing to remember with this option is that it needs to be at the end of the video filter chain. Details can be [seen here]("http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-dvd-mpeg4.html#menc-feat-dvd-mpeg4-muxing-filter-issues").

**Edit**: Corrected the 'hardup/harddup' error.

Andrew

---

### Post by fatalGlory on 2009-02-03
Gave it a try, also tried -vf softskip, no dice.  BTW, for anyone trying it, its actually "harddup" (note the double d).  Thanks anyway.

**EDIT:** I think I may have found a fix.  For the movie I have been trying to encode while writing this, audio sync problem seems to go away if I use the -noskip with mencoder.  I still get a whole lot of "Skipping frame!" messages, which seems odd, but the sync is right at least.  Also seems strange that I would need to do this for some dumpped VOB files but not all.

Still, if it works it works ;)

**EDIT 2:** On closer inspection, adding -noskip makes the audio sync up in mplayer, but when I try to play the movie in Totem (and probably other players), I get the reverse problem, audio that once lagged behind now plays prematurely.  Better to encode for non-mplayer players I guess since mplayer has such simple support for setting the A-V delay during playback.  Also points to a problem with mplayer's playback rather than encoding I suppose since other players handle the encoded file properly.

---

### Post by fatalGlory on 2009-02-03
Solution found!  It appears AVI files work better with constant bit rate audio than variable bit rate audio.

After reading [this thread](http://lists.mplayerhq.hu/pipermail/mencoder-users/2005-July/001294.html) (about VBR vs. CBR and the AVI container) I decided to try encoding with CBR (constant bit rate) mp3 audio and now the video playback is fine in all players.

I used this command:```
mencoder movie.VOB -ovc xvid -xvidencopts bitrate=1024 -oac mp3lame -lameopts cbr:br=128 -o /media/scratch/Videos/Movies/movie.avi
```

All good now.

---

