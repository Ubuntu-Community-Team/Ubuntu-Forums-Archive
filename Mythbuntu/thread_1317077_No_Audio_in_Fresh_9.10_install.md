---
title: "No Audio in Fresh 9.10 install"
date: 2009-11-06
forum: Mythbuntu
---

### Post by rnelson0 on 2009-11-06
I have been running 8.04 on my backend/frontend machine for a while now and I decided to do a fresh install of 9.10. Everything seems to have installed perfectly. However, I get no audio. I've tried playing video files, mp3 files, nothing, no sound. I checked the mixer included with 9.10 and it looks like nothing is muted or turned down.

When I open the mixer app from Applications > mixer, it lists my device as HDA Nvidia (ALSA mixer).

I'm comfortable using the command line to solve this, I just don't know how to solve it or where to start. 

Can anyone help me with this?

---

### Post by dacodo on 2009-11-06
I had the same problem in rc2 I installed the pulse audo volume controll and it fixed it.

but in the finally release i have the same problem and the pulse controll didnt fix it. I've installed ubuntu 9.10 and it doesnt have any audio problems (but lots of randoem lockups).

Have you tried exporting:
export EXPERIMENTALLY_ALLOW_PULSE_AUDIO=1

I've seen some reports of that helping some people.

---

