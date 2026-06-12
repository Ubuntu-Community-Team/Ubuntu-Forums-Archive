---
title: "No sound in pidgin, works everywhere else."
date: 2008-08-08
forum: Multimedia Software
---

### Post by helwitch on 2008-08-08
The sound works fine on my system for everything except pidgin. This includes multiple applications playing sound at the same time (firefox youtube video&vlc media player is how I tested.) However, I can NOT get sound to work in pidgin. Anyone know what I need to do? Since sound works otherwise, I'm figuring it to be a configuration problem. I'm on kubuntu 8.04

---

### Post by helwitch on 2008-08-17
Anyone got any hints? Is this in the wrong forum, should I repost in another forum?

---

### Post by abbasali on 2008-08-21
Try these two options.

1. Install Gstreamer (Movie Player) from Add/Remove Programs
2. [http://blog.turbulentsky.com/2007/12/pidgin-has-no-sound-in-ubuntu-gutsy.html](http://blog.turbulentsky.com/2007/12/pidgin-has-no-sound-in-ubuntu-gutsy.html)

I had the exact same problem and both the above mentioned solutions worked for me.

---

### Post by helwitch on 2008-08-21
Thanks! The laptop I was having this problem on had the ac port burn out, so it's off being fixed now, but when I get it back, I'll give those a shot!

---

### Post by abbasali on 2008-08-22
Sure - Try any one option (I wasn't clear in my first post :) )

---

### Post by helwitch on 2008-11-08
Hey, thanks! That worked. I just now got back to 'ok, everything major works, what's still broken' after getting the laptop back, but the aplay %s command solution works perfectly!

---

### Post by fellrond on 2008-12-22
i solved this problem changed sound play method to 'Command' and inputed 'aplay %s' for it, thanks!

---

