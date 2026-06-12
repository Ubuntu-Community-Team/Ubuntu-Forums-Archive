---
title: "Amarok not playing any audio"
date: 2009-11-04
forum: Multimedia Software
---

### Post by ucal on 2009-11-04
So I've used amarok before on a different computer, and it is indeed amazing.  However, on this computer when 9.04 was installed it didn't play audio at all.  It just attempts to play, fails, and moves on to the next song in the playlist, which it will fail on as well.  These are .m4as (off of itunes before the DRM lift) and .mp3s

Now, in 9.10 it just doesn't even attempt to play it at all.  I set up a play list, click play, and nothing happens.

Also, is there a way to remove the splash screen, or move it?  It keeps appearing above the KDE wallet notification, and won't go away until I click on that notification, but it's below the splash screen, making clicking on it a tedious process to go through everytime I want to use amarok. Why the hell does amarok even need kde wallet services?

I know this isn't a sound problem (though the upgrade has caused those too D:)  because rythmbox plays the music just fine.  

Finally, I guess my last question is if there is anyway to go back to the old sound control interface.  Where you could select specific devices to use for sound output.  (Devices is definitely the wrong word here).  Like, in 9.04 I could set it so that the front and base speakers on the laptop played music, but nothing else, or that the surround played it and nothing else (the only way to get headphones to work in 9.04 for me).

EDIT:  Solved the not playing problem with a post in another thread.  Had to install some libraries.

---

### Post by The Black Page on 2009-11-05
can you post the thead where you found the fix please bro i've got an almost exact problem here though i'm a bit dicey on just installing a generic fix as from what i've read on the board to date coz i'm amd 64 ubuntu (not kubuntu) 9.10 & want to install as much 64 bit specific plugins as possible this early in the install (flash etc.).is there an amarok specific fix for this bug anywhere guys? seems not uncommon.i hit it on 9.04 32 bit the 1st time i installed it yet the 2nd time on 9.04 i loaded my mp3's a folder at a time & it kicked just fine but now my music folder is 20 gig so thats a laborious process indeed if in fact its gone down from overload but i read it handles mass dumps no probs?tried the xine thing to no avail but maybe i botched it up.audio everywhere else is fine.any help would be much appreciated cheers..

EDIT: found the fix here thanks guys post 6 kudos to the poster..

[http://ubuntuforums.org/showthread.php?t=1135082&highlight=Amarok+audio](http://ubuntuforums.org/showthread.php?t=1135082&highlight=Amarok+audio)

sudo apt-get install libxine1-ffmpeg

---

