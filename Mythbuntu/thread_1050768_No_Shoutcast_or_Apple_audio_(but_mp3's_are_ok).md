---
title: "No Shoutcast or Apple audio (but mp3's are ok)"
date: 2009-01-26
forum: Mythbuntu
---

### Post by rastoboy on 2009-01-26
Ok this is a little weird--I can get Shoutcast streams--at least I see the little sound meter thingy rocking and rolling--but I get no audio.

I got audio working with the mp3 player by going into settings and setting output for the internal player to /dev/dsp1.  And that works fine.  But for some reason not Shoutcast streams or Apple movie trailers--though I can see the images.

I'm just not even sure how to go about debugging this, as I'm still quite new to mythtv.  Any input would be greatly appreciated!

---

### Post by rastoboy on 2009-01-28
Ok, the Oracle (strace) showed me that it's spawning mplayer to play the stream, so I was able to edit /etc/mplayer/mplayer.conf and set the audio device in there.

Now I wonder--how can one change the player it uses?  I'd like to set it up with Amarok so I can use the visualizations there.  Any ideas?

---

