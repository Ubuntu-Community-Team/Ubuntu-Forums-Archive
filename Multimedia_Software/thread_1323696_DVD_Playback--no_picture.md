---
title: "DVD Playback--no picture"
date: 2009-11-11
forum: Multimedia Software
---

### Post by Holonet on 2009-11-11
I've been having a lot of trouble lately with video playback.  I've installed all the medibuntu junk, libdvdcss2, libdvdread4, and all those.  Tried Mplayer, VLC, the default movie player, and they all act the same way.  I try to play a DVD, and it works, I hear the sound, but I have just a blank, black screen for a picture.  

I've noticed this problem the past couple versions of Ubuntu, though I'm not sure if that's the only variable...but not until now have I really tried to fix it, and nothing works.

I also tried uninstalling the brasero/rhythmbox library...to no avail.
 
These are DVDs which I've played on Ubuntu before...so it seems that either there's some cryptic avenue I haven't explored, or another case of Ubuntu classic bleeding edge...If the rifle jams, fix it on the way to the battlefield...release, release, release!  Anyhoo, enough of my ranting...

If anyone has a clue what idiocy has befallen me, I'd be most appreciateive :).

---

### Post by HappyFeet on 2009-11-11
You didn't happen to "upgrade" to karmic, did you?

---

### Post by Holonet on 2009-11-11
Why yes, yes I did...and I see the implication...  and I've just read in another post that upgrading is known for breaking things...  Thank you...I'll report back after I endure the tedium.

---

### Post by andrew.46 on 2009-11-12
Hi Holonet,

> **Holonet said:**
>   I try to play a DVD, and it works, I hear the sound, but I have just a blank, black screen for a picture.

I wonder if there is a difference if you alter the default video out device? With vlc for example this can be seen:

Tools --> Preferences --> Video --> Output

and a safe option is sometimes 'x11 Video Output'.

All the best,

Andrew

---

### Post by Holonet on 2009-11-12
Alright, I've done a clean install, and it changed nothing--exact same problem.  However, Andrew, what you suggested was helpful.  I changed the output in VLC to the openGL, and it worked.  However, it still leaves the question of why it happens to begin with, and has to be worked around.  Ubuntu should be able to play the DVDs without some program-specific workaround.

I did leave my home directory on a separate partition.  Is it possible anything in there would cause the problem despite the otherwise clean install?

---

### Post by andrew.46 on 2009-11-12
Hi Holonet,

> **Holonet said:**
>  However, Andrew, what you suggested was helpful.  I changed the output in VLC to the openGL, and it worked.  However, it still leaves the question of why it happens to begin with, and has to be worked around.

Good to hear there has been at least some success :). I am puzzled too as to why the usual default of xv is so troublesome in various versions of Ubuntu, it is a problem on my own system as well.

Andrew

---

