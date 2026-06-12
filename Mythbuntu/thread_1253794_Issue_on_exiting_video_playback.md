---
title: "Issue on exiting video playback"
date: 2009-08-30
forum: Mythbuntu
---

### Post by Robert_Br on 2009-08-30
Greetings.

I like to think I know my way around linux pretty well, but I'm less than a day into messing with mythTV, so this may be a stupid question. Mr. Google has turned up no answers, so I'm asking here.

I installed mythbuntu, and I'm using a logitech harmony 550 remote with a homebrew serial receiver. I followed [these]("http://www.mythtv.org/wiki/Logitech_Harmony_Generic_Setup") directions and my remote performs as expected with one exception. I imported some VIDEO_TS folders I had laying around into mythtv's video directory. It picked them up and plays them fine, but when exiting the playback by either pushing stop or exit on my remote, it not only stops the playback but the frontend as well. Then, I have to VNC onto the machine and restart the frontend, so this is obviously PITA.

I don't know how it behaves with recordings from cable as my tuners haven't arrived yet, but the exit button functions normally within the mythTV menus, so I don't really think it's a remote issue.

Any ideas?
[ ]("http://www.mythtv.org/wiki/Logitech_Harmony_Generic_Setup")

---

### Post by Robert_Br on 2009-08-30
I saw another similar thread after posting this one in which removing pulseaudo has fixed the issue for some. Pulseaudio is not installed on my system, but libpulse or something to that effect is. However, removing it would also nuke xine and mplayer, so that doesn't seem to be an option.

---

