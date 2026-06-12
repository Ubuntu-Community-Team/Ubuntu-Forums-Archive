---
title: "VLC power management issue"
date: 2013-05-23
forum: Multimedia Software
---

### Post by gowings83 on 2013-05-23
So I'm using Ubuntu 13.04 right now, latest VLC and have my power settings to turn off the monitor after 1 minute.  It's that short so an image won't get burned in to my tv when a video is done.  I found a few posts on fixing this but none worked, probably since the most recent I found was over a year ago.  Here's what I've tried based on those posts.  I turned off Inhibit power management and Disable screen saver.  Now the monitor turns off after the movie is done, but also during the movie.  I've tried every combination I can and it either does both or won't turn off the monitor when done.  However if I just load VLC without a video the monitor turns off as it should.  So what in the world can I do to fix this.  As I said I don't want an image burned in to my TV, I often pass out watching a movie.  I'm trying to FINALLY replace Winblows with Ubuntu since I so much prefer it.  I'm just trying to see if all issues I had with 12 were fixed.

---

### Post by ohnonot on 2013-05-24
sounds like a case for caffeine (the app, not the drink ;-).

but basically the problem remains, because, iirc, vlc stays on after the movie ends. maybe that can be changed from inside vlc? did it work as wanted under windoze? vlc i mean?

anyhow, mplayer exits after ending playback, which would allow caffeine to re-activate screen blanking.

also, generally you don't need both screensaver and power management. consider ditching the screensaver, like uninstalling it.
also take a lok at xset.

---

### Post by gowings83 on 2013-05-24
Hey im not exactly sure what you mean by some of this.  I can tell you VLC didnt have that issue in windows although i didnt have it set to turn the monitor off, just load up the screensaver.  As far as i know theres no screensaver any more.  As for caffeine what exactly is that for?  Ill give mplayer a shot i just knew vlc played everything like stuff i download like mkv and mp4.  I will give your advice a shot when i get home later.  Thanks

---

### Post by ohnonot on 2013-05-24
i'm sorry i was jumping ahead.
anyway i had a look at vlc's preferences; change "show settings" to "all", then go to playlist in the tree. there you will find an option called "Play and exit". check that. save. exit vlc. try if everything is behaving the way you want it now.

if not, you can still consider using caffeine or trying out different media players - mplayer is just as versatile as vlc, but it has no gui. there's also xine-ui, which is very good and powerful; the ui is ugly, though. 
there's also versions of mplayer with gui.

---

### Post by gowings83 on 2013-05-24
Thanks a ton ohnonot, what you said for vlc worked.  It doesn't close though, just goes to a black screen and then the monitor turns off as it should.  I don't have to worry about anything burning in to the tv, even though I use the timer to turn it off sometimes shows dont match the times available.

---

### Post by ohnonot on 2013-05-25
strange, on my machine checking that option makes vlc exit completely after playing the last item in the playlist.

anyhow, glad to be of help. happy falling asleep in front of the tv!

do you think this could be marked as solved (top right, thread tools)?

---

### Post by gowings83 on 2013-05-25
Sorry it seems not.  My son watched a movie last night and it stayed on the last frame of the video, didn't even exit from the full screen mode.  I guess the last video was a black screen on the last frame.  In any case the monitor still turned off so it's half solved.  It's good enough for me :)  As for the solved thing, there's no option for that in that menu.

---

### Post by ohnonot on 2013-05-25
try caffeine, together with the vlc option i described earlier!

and there *is* a "solved" option in thread tools on top of the first post of the thread.

---

