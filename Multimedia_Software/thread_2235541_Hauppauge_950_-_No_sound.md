---
title: "Hauppauge 950 - No sound"
date: 2014-07-21
forum: Multimedia Software
---

### Post by dianemeeks on 2014-07-21
I've had this problem time and again, but none of the old methods have worked this time, so here I am again. I recently installed Trusty on a new build and hooked up an Hauppauge 950 TV tuner. I have picture bu no sound in tvtime. Normally, I would try it in VLC, but it's a whole other can of worms. When I select the capture device in VLC, nothing happens, no errors, no video, nothing. I'll settle for sound in either program. Any suggestions?

---

### Post by dianemeeks on 2014-07-25
Additional information:
When I launch tvtime using "tvtime | arecord -D hw:2,0 -f S16_LE -c2 -r32000 | aplay -" for a few seconds the sound launches. I don't hear it, but it registers that aplay is running in the sound settings. It then shuts down immediately, making me think it isn't the usual sound problem. Maybe a different command is needed?

---

