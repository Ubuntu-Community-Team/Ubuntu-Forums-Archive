---
title: "Odd volume control glitch"
date: 2009-06-22
forum: Mythbuntu
---

### Post by mathog on 2009-06-22
We encountered a very odd volume control glitch this morning.  

Mythtv is completely controlled via lirc from a universal remote.  This morning after booting, in Mythtv the vol+ key was not working, but the vol- key was.  When vol+ was pressed nothing would happen (the volume indicator did not appear, and if already up from a vol- press, would not increment up.)  All other keys tested were working normally.  This was not a bad key problem with the remote, since setting it to control the TV let vol+ work to change the TV's volume.  A reboot partially fixed the problem - afterwards vol+ worked for a few seconds, up to about 94% volume, then stopped working, as before.  Eventually a "fix" was found:  turning Mute On, then Mute Off, reenabled the vol+ key.

I am not quite sure what might have caused this, but recall that the DVR was turned off by pushing the power button instead of exiting out through MythWelcome last night.  We do that often, and this is the first time the vol+ key has glitched like this.

This "feels" like an uninitialized variable issue.

---

