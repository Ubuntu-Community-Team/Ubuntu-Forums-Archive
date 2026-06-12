---
title: "Mythtranscode fails on all recorded programs"
date: 2011-02-15
forum: Mythbuntu
---

### Post by kheston on 2011-02-15
Mythtranscode fails on every video I record.  I'm using an HVR-2250, OTA programs only, 10.04.  Is there anything I can try to fix/diagnose what's going on?

---

### Post by nickrout on 2011-02-16
logs?

---

### Post by kheston on 2011-02-16
The logs aren't particularly helpful, the only logged message is "Unrecoverable Error."  I read in a post that the video quality could be an issue.  When I play the vids in mplayer, they are indeed glitchy (VLC won't even play them).  Is that my issue?  If so, I'm wondering why ALL of my recorded shows aren't good enough for mythtranscode and mythcommflag to work properly.  Any pointers appreciated.

---

### Post by nickrout on 2011-02-16
> **kheston said:**
> The logs aren't particularly helpful, the only logged message is "Unrecoverable Error."  I read in a post that the video quality could be an issue.  When I play the vids in mplayer, they are indeed glitchy (VLC won't even play them).  Is that my issue?  If so, I'm wondering why ALL of my recorded shows aren't good enough for mythtranscode and mythcommflag to work properly.  Any pointers appreciated.

yes transmission errors could definitely cause this sort of problem.

Check all your connections, aerial down to back of the PC and think about a masthead amplifier.

---

### Post by kheston on 2011-02-19
Looks as though my video quality was really bad and was causing mythtranscode and mythcommflag to go out to lunch. 

I made a few changes, including relocating my antenna (I'm OTA only) and running an update (I'm on 10.04) and making sure it completed. 

I'm still getting some video encoder glitches (presumable, with the DTV signal drops), but mythtranscode and mythcomflag haven't failed for a couple of days' worth of recordings.

---

