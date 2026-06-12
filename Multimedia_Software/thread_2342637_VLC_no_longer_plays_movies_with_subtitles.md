---
title: "VLC no longer plays movies with subtitles"
date: 2016-11-08
forum: Multimedia Software
---

### Post by peyre on 2016-11-08
I've been using subtitles a lot, but they're no longer working properly.

[LIST=1]
[*]I have some .mkv files ripped from a home-authored DVD--an interview of my grandfather, who had a really thick accent and spoke in other languages sometimes.  I'm going through them and creating subtitles in .srt files so family members can follow him better when watching the videos.
[*]When I watch movies on my computer (mostly DVDs from Netflix), I usually turn on the subtitles so I don't miss any of the dialogue.
[/LIST]
So until recently, VLC was rock-solid at handling subtitles--it *just worked*; it was top-notch for the job.  But now--I think this happened when I upgraded to Xubuntu 16.10--it doesn't play them right.  The .mkv files show one subtitle, then the picture gets kind of blocky, then stops altogether, no more video or subtitles (though sometimes it shows a grainy moving image afterward, or another subtitle or two now and then).  The movie DVDs get blocky--the motion stops and starts constantly.  Both the files and the DVDs play fine when I have subtitles turned off.

So what can I do about this?  Am I missing a plugin or codec?  Is there a setting I can change in VLC to fix this, or something else maybe?

---

### Post by mc4man on 2016-11-08
No idea, vlc has a history on issues with mkv.
Maybe try - 
Open vlc > Tools > Preferences > Input/Codecs & for Hardware-accelerated decoding > Set to Disabled in the dropdown
Click save, close & re-open vlc,  try your subs & see.

---

### Post by peyre on 2016-11-08
That didn't do it, but it was a good idea, thanks.

---

### Post by shantiq on 2016-11-09
peyre it seems VLC in the last 2 years or so is no longer the man it used to be   may i suggest using

```
sudo apt install mpv
```


instead/faster/more stable

subtitles :
V for visibility
J for toggling between subs

---

### Post by peyre on 2016-11-20
Thank you, shantiq!  Your idea of finding another video player seems to have done the trick.  mpv seems a little bare-bones for me, but someone else on another forum suggested SMPlayer, and so far that seems to be an excellent drop-in replacement for VLC.  It's a shame!  VLC was The Bomb, but they've gone and messed up a Good Thing.

---

