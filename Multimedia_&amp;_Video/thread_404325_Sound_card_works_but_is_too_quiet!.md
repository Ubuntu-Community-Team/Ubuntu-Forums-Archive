---
title: "Sound card works but is too quiet!"
date: 2007-04-08
forum: Multimedia &amp; Video
---

### Post by Aro on 2007-04-08
Hi everyone :)

I have two sound cards in my machine. One is an integrated sound card that no longer works, and the other is a cheap c-audio pci soundcard which does indeed work.

I figured out how to switch which card is being used through volume control, however recently I've noticed a problem with my sound.

It's SO quiet!!
I plugged in headphones and they were too quiet to hear a lot of videos I watched on youtube...I had to put the speakers to full volume, set volume control to full volume, and set the video player's volume to full...then stick the speaker RIGHT next to my ear...and even then I heard more static than actual sound.

I'm pretty sure my problem is software based, and not hardware...but I will troubleshoot again later and be as sure of this as I can. 

My question is, in linux (ubuntu 6.06 specifically), other than the volume control on my speakers, the volume control in 'volume control', and the volume control in whatever player is playing whatever media file at the time....

Are there ANY other volume control settings that I should be checking..somewhere?
I don't know of any others.

Thanks!

---

### Post by heimo on 2007-04-08
You could try to check if you have all the sliders up and channels not muted in alsamixer. If the non-working integrated soundcard is still detected as the first sound device, you should invoke alsamixer with -c1 flag (that's c and number one).
```
alsamixer -c1
```Use arrow keys to move and change sliders and tab key to change between playback, capture and "all".  Key M mutes / unmutes channels. escape to quit

---

### Post by Aro on 2007-04-09
I turned everything up to 100% (aux, line in, etc)

Master was already 100% and nothing was muted.

After I turned the other options up I played a song again and it played at full volume.
Unfortunately, everything (including my speakers) were set to maximum volume. 
So i'm kind of deaf right now and my speakers are on fire...

But it all works perfectly!

Thank you very much for your help :):guitar:

p.s. when I ran "alsamixer -c1" i got the following message:
>   wrong -c argument '1'

---

