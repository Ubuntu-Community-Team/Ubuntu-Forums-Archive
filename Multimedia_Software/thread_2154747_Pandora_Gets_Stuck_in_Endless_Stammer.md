---
title: "Pandora Gets Stuck in Endless Stammer"
date: 2013-06-15
forum: Multimedia Software
---

### Post by Iggy64 on 2013-06-15
I am running Bodhi Linux = Ubuntu 12.04 with e17 desktop.  I play Pandora primarily using its own web interface through Firefox.  Infrequently, but still disconcertingly, the sound output will lock into what I would call a "stammer."  It is as if a single note just keeps repeating itself endlessly, like a real tight echo, but without any decay in amplitude.  Completely locked up.  To stop it, I need to close Firefox.  When I reopen and Pandora restarts, all is OK.

I can't say I totally understand how Pandora actually works.  From my research, it SEEMS like Pandora temporarily downloads a file onto my hard disk, then plays it through my resident Flash player.  As far as I can tell (and I am FAR from being an expert, as you can see), Flash does not output through GStreamer, but apparently directly through ALSA.  As the stammering does not seem likely to be due to a file download issue, this must be some sort of problem with either Flash or ALSA.  But again, I assume others in this forum will know much more about this than I do.

I can add that I played Pandora through Firefox for a few years under Windows XP and am rather certain I never encountered this problem.  I converted to Ubuntu (and then the Bodhi derivative) starting a couple of years ago.

I cannot say with certainty that this problem has never happened with other players in Linux.  I use Audacious and Aqualung (which output directly to ALSA) and Clementine (which sinks to GStreamer).  I just can't remember whether I have had this stammer occur with any of them.  I play Pandora much more than any of those.

I wonder if anyone can suggest a possible cause and/or cure for this problem.

I would also be very grateful if someone could explain exactly how Pandora plays its music on my machine.

---

