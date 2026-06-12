---
title: "SMPlayer subtitle functions not functioning"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by darweth on 2007-11-29
Evening!  Has anyone else tried delaying or speeding up subtitles within SMPlayer?  The Z and X buttons are the shortcuts that provide this function.  I tried it in the SMPlayer from the official repos + other packages acquired on the net.  Failure on all counts.  This function worked fine on my previous Arch box.  Any ideas?

---

### Post by rvm4000 on 2007-11-29
First check if you have assigned the keys Z and X to the actions dec_sub_delay and inc_sub_delay in the shortcut editor in preferences.

Then check if in the console messages (or smplayer log in options->view logs) you can see lines like these, when you press those keys:
```

Core::decSubDelay
Core::tellmp: 'sub_delay -0.7 1'
Core::incSubDelay
Core::tellmp: 'sub_delay -0.6 1'

```

---

### Post by darweth on 2007-11-29
Yes, I can see those events in the console. :)  I not only tried the shortcuts btw, but also the drop-down menu way.  

I suppose those items popping up properly in the console point to the function actually taking place but it doesn't seem to be doing anything.  Maybe it is not compatible with .srt subs?  Is it .sub/.idx combo only?

---

### Post by rvm4000 on 2007-11-29
Those options should work with srt files too.

What version of mplayer do you have installed?

---

### Post by darweth on 2007-11-29
MPlayer 1.0rc2-4.1.3 

This is all weird. :)  I have tested all other shortcuts and functions and they work fine.

---

### Post by rvm4000 on 2007-11-29
Yes, this is very strange.

I don't have version 1.0rc2 installed right now in linux, but I have several other builds and I never saw this problem. Even the old 1.0rc1 works properly.

Anyway, does the sub delay confirmation appear in the OSD? (you need the OSD activated)

[img]http://img140.imageshack.us/img140/1540/delay2ct0.jpg[/img]

**Edit: ** I've just compiled 1.0rc2 and it works perfectly :confused:

---

### Post by darweth on 2007-11-30
Well, it appears to be working now oddly enough.  I don't know!  haha.  It seriously did not work on one film and .srt combo I was testing it on.  The subtitles were mistimed and trying to delay the .srt had zero effect.  But I downloaded another movie and it appears to be working with that one so I guess this was all for nothing.  :O  

I don't know.  Could that .srt file have been bonkers?  Seems a bit odd.  

I appreciate your assistance. :) :)

---

