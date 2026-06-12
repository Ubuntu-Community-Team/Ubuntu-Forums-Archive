---
title: "manually set frequency for video tuner [v4l]"
date: 2009-04-06
forum: Multimedia Software
---

### Post by Til_Valhall_vi_drar! on 2009-04-06
hi, i have a Hauppauge HVR 4000 card, and its working fine.

The thing is that i want to manually set the channel on the tuner so i can get the stream... well here is an example of what i mean:

if i do this

mplayer tv://

its working fine, mplayer sets the frequency, and plays it...

I want to do something like this:

[command to set channel] [frequency] /dev/videoX


and btw, i ofcourse can't 

cat /dev/video0

which gives me an input/output error.

the thing is that i have this card on my server and i want to stream it, but before recommending some programs to do that, i really want to learn how to do it in a *real* low level way...

i am right when i say that the i/o error of catting /dev/video0 is because of i haven't tuned in on a channel right?

do i have to do something like this:

printf "\x[somebinary]">/dev/video0

then i can:

cat /dev/video0 | nc x.x.x.x 1024

??

or do i even have a clue??

---

