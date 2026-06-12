---
title: "Rhythmbox won't play certain MP3s or won't pause"
date: 2011-01-12
forum: Multimedia Software
---

### Post by PRupp89 on 2011-01-12
I recently tried changing from pulseaudio to alsa, but decided to switch back once I found out how to fix the original issue I had with pulseaudio. I had never used rhythmbox before, and imported all my music into it, but there are a few random songs that won't pause when I hit pause, and I can start playback of another song but the first one is still playing until it reaches the end. Other times those same songs will be silent with some crackling in the background. I've already switched gstreamer-properties back over to using pulseaudio, but is there something else I may need to switch? or addtional plugins that I may need? Most mp3s/other formats play fine, its just a select few giving me issues. I'm using 10.04 with rhythmbox 0.13.1 on a lenovo y550. 
Thanks!

---

### Post by elmanuelito on 2011-01-14
I think I might have the same problem than you: 
- Rhythmbox won't pause on some songs, and If asked to play another song it will just play it on top.
- Also, I have several mp3 that when played just produce crackling for the whole song, no music (although they work with vlc).
I had this for a couple of month, I'm only starting to have a look at it. 
I'm using Rhythmox 0.12.8 on debian squeeze.
I'll try to have a look at the debug output when it happens (rhythmbox -d)
I hope we'll figure this out!
Regards

---

### Post by elmanuelito on 2011-01-14
Ok, I might have found a solution to stop this.
[B]Are you using the crossfading?
Try desactivating it to see[/B]. It did the difference for me.

I've done a small rhythmbox database with only 2 mp3. One which I know always work and the other one which causes problems. I ran rhythmbox in debug mode with and without fading(after restarting), and trying to pause either the good MP3 or the bad one. So that's four tests. 
Each time I ran
rhythmbox -d 2>log
(testing pause)
cat log| cut -c24-|egrep "rb_shell_[ps]|xfade|controls|slider|set_state"

When xfade is activated (with the good and bad mp3), the debug outputs are identical till the step  "syncing with source"
Then for the bad MP3 i got a lot of
[slider_moved_callback] rb-header.c:676: slider is not dragging
Whereas for the good one:
[volume_changed_cb] rb-player-gst-xfade.c:970: stream file://... fully faded out (at 0.000000)
[volume_changed_cb] rb-player-gst-xfade.c:995: posting rb-fade-out-done message for stream file://...


I don't know if crossfading is the source of this problem. Probably. 
Probably also this won't occur with ogg format...

Let me know if it worked for you.

---

### Post by DavidRaid on 2011-01-14
Same problem here, I'm running Ubuntu 10.10, Rhythmbox 0.13.2 from a PPA. 

I had the same problem before adding the PPA when I had the newest Rhythmbox from the official repos, and installed the newest in the hope of fixing the problem.

I'll be playing songs and then the next one will crackle, pausing stops the crackle but nothing else will. Then when trying another song, the first song will play over it. 

I've tried to reproduce this problem by skipping through songs, but it hasn't worked. If it is the crossfading then that would explain why it only happens when a song ends and switches to another.

I'll try turning off crossfading and see if that works.

---

### Post by DavidRaid on 2011-01-14
Same problem here, I'm running Ubuntu 10.10, Rhythmbox 0.13.2 from a PPA. 

I had the same problem before adding the PPA when I had the newest Rhythmbox from the official repos, and installed the newest in the hope of fixing the problem.

I'll be playing songs and then the next one will crackle, pausing stops the crackle but nothing else will. Then when trying another song, the first song will play over it. 

I've tried to reproduce this problem by skipping through songs, but it hasn't worked. If it is the crossfading then that would explain why it only happens when a song ends and switches to another.

I'll try turning off crossfading and see if that works.

---

### Post by DavidRaid on 2011-01-14
Sorry about the multiple replies there, my connection cut off and a refresh of the page seemed to have caused it. This was a third copy, but I've edited it to this rather than post a further message. <.<

Sorry!

---

### Post by New00Folder on 2011-02-16
I had the same problem with Rhythmbox 0.13.1 in Ubuntu 10.10.
Surprisingly, disabling cross-fading does work.
Thanks a lot, elmanuelito.
But there's an additional problem of Rhythmbox quitting when I close the window without a song playing or paused. Earlier in Ubuntu 10.04 and 9.10 this was not an issue; I could close the window whenever I liked and it would still be there on the panel.
I wish someone would find a way to disable this lousy "Import error" forever.

---

### Post by New00Folder on 2011-02-17
Nope, that was a false positive. Now different songs crackle. And sometimes even restarting rhythmbox sets things right but sometimes not. It's totally erratic.
Rhythmbox used to be my favourite music player; I hope someone finds a fix soon.

---

