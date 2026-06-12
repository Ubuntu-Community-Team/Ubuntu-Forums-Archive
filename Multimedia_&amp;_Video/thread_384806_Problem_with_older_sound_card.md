---
title: "Problem with older sound card"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by gaalderman on 2007-03-14
I just installed 6.10 on an older workstation I have.  The install went fine and all my hardware was detected just fine, except for the sound card.  I have an older ISA SoundBlaster 16, which I was able to get working by adding snd-sb16 to /etc/modules.  Now the card seems to work, and will play sounds like the startup and logoff sound just fine.  However, when I try to play a DVD, the DVD will play fine but I'll hear a periodic click or pop on the audio:  "Click...click...click...click".  This seems to happen regardless of the player application I use.

When I play an MP3 file in Totem, the same thing happens:  the file will play, but I'll hear a click or pop repeating over and over again.  Very irritating.

Any ideas?  Is it just an old decrepit sound card and a new one will solve the problem?

Thanks,

GAA

---

### Post by gaalderman on 2007-03-15
Just in case any one was wondering, the solution was simple.

Run:  
sudo go_to_Wal-mart
sudo buy_modern_soundcard -u cheap_*******

Now it works fine.  Object lesson:  the old sound card was made in 1996.  It is a doorstop.

GAA

---

