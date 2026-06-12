---
title: "Mythtv front end crashing after pausing video"
date: 2007-02-01
forum: Multimedia &amp; Video
---

### Post by wrethemyr on 2007-02-01
This is a bit of a weird problem im having with mythtv.

About half the time, when watching livetv or pre-recorded shows (transcoded) the myth front end will crash when i try and resume playing after pausing.

Situation one:
I am watching tv, i hit pause.  video pauses, everything is happy.  I hit play, the screen goes dark, the audio starts playing normally, screen flickers and in 2 seconds or so, the video comes back in, perfectly in sync with the audio.  Yay

situation two:
Same as above, except after the 2 ish seconds, the audio stops... the screen stays blank (or sometimes turnes solid blue) and then X apears to die.  The cursor flickers in and out with the waiting symbol, and i can still move it around, but i can never fully recover (I'm pretty sure the backend is still running)  Ctl+alt+bksp doesnt recover from it... eventually the system reboots.

I also experienced similar issues with straight mplayer outside of mythtv

more info:
hitting the skip forward button over comercials seems to work flawlessly, and same if i hit rewind and it rewinds to the beginning and just starts playing automatically.  If i hit ff or rewind and then hit play (to pause it) and play again, i get the crash.

my system:
mini-itx pentium M 1.6ghz
1 gig of ram
onboard intel gfx card using dvi to hdmi out to my tv
onboard sound, digital coax
haupage pvr 500 tuner card
320gig HD, (~12 gigs / reiserFS, 2gigs swap, the rest jfs)
running Feisty fawn (though the problem also occured in edgy)

I have tried disabling real time threads in myth, and played around with it a bit.  It seems to happen more when the disk is working harder, but it could be coincidence.

Any help, or a direction to try would be apreciated, thanks

---

### Post by Neobuntu on 2007-02-03
I am having the same problem. Please help. I'm not sure where to turn.

---

### Post by Neobuntu on 2007-02-08
I read about an issue with Via motherboard chips and dumb tuner cards (not yours) causing lock ups. 

I have no idea if this is true. But it's all I've got.

Can anyone help?

---

### Post by wrethemyr on 2007-02-08
except that mine is an intel.

I am wondering, however, if its not something to do with my tv/dvi to hdmi thing.  Maybe trying it with a traditional monitor and seeing what happens.  Or possibly something with my xorg.conf not being setup correctly for my tv.  Every time i try and tweek it though, i just end up with a broken xorg.conf file and an unhappy computer.

(the reason i suggest this, is with my setup, whenever i play a video normally, or go into mythMusic (where it loads a visualization) the screen blanks for a few seconds (the audio starts immediately)  and then comes back.  I dont remember this happening when it was hooked up to a normal monitor)

just a thought

---

### Post by ridshack on 2008-01-19
Have a very similar sounding  issue. Everything seems to work fine until I do a rewind and then pause, then play. The video will not play but skip randomly in fast forward and the audio will sound like 10 movies playing at once. Also at that point the front end will not accept anymore commands but I can still SSH in.

What do you guys get in your log files when the crash occurs? 

/var/log/mythtv/mythfrontend.log

I got several of these at the moment it occurred.

> NVP::AddAudioData ( ) : p1 : Audio buffer overflow, audio data lost! 

Im going to try and disable my on-board audio in the bios. 

Rid

---

