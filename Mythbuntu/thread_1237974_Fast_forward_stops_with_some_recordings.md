---
title: "Fast forward stops with some recordings"
date: 2009-08-12
forum: Mythbuntu
---

### Post by laffinet on 2009-08-12
Fast forward (or rewind for that matter) seems to be hit and miss on my machine. On some recordings it works fine while on others I encounter some weird problems. 
Forwarding starts ok, but after a few seconds the picture becomes "blocky" and soon after forwarding stops. Hitting the fast forward button again resumes the fast forward from that position, although at a higher speed.
I've also noticed that when hitting play after forwarding stopped that playback doesn't start at that position but a few seconds earlier in the program.

Any ideas ?

BTW: I've got 3 hard drives, each with recordings on them, however this problem doesn't seem to be related to a specific drive.

---

### Post by SiHa on 2009-08-12
> I've also noticed that when hitting play after forwarding stopped that playback doesn't start at that position but a few seconds earlier in the program.

Not sure about the actual problem, but this behaviour is normal. Mythtv will skip back by a set amount after hitting 'play' this allows for your recation time, and I love this feature! You can change the amount in the frontend setup somewhere. Note that the amount is skips seems to be the accellerated FF/REW time. ie if it skips, say 300ms, at 120x it will skip back much further than at 10x.

---

### Post by laffinet on 2009-08-12
Yeah, noticed that on all fast forward (or rewind), but on recordings with "dodgy" fast forward the amount of skipping back seems to be a lot more than usual.

---

### Post by SiHa on 2009-08-12
Oh. OK. Sorry.

Butting out.

---

### Post by tshannon on 2009-08-12
I'm sure you've done this, but I'm just tossing this out there.  I know they keep some sort of seek index in the database to improve ff performance, and optimizing your database tables can improve seeking performance.  

I remember be disapointed in how "dodgy" my seek performance was, then I read about the optimize tables script, and that fixed it.

---

### Post by laffinet on 2009-08-12
Are you referring to the "optimize tables" button in the Mythbuntu control centre ? 
I've got a tick in the "enable daily MythTV database optimization/repair" box, which should do the trick, right ?
Or is there another script ?

---

