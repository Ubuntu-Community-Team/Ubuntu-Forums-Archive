---
title: "Can't believe it..everything working well...then.."
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by thered on 2007-11-03
The sound packs up.

In front of my very eyes(ears). Playing a youtube file it ust stopped working! I've been running Ubuntu ok for a month or so without issue.

It started with having to turn the volume to max then stopped all together.

I can hear speakers crackling, especially on boot up.  I have changed nothing, nothing at all.

Sound OK if boot to windoze, so I assume not a hardware problem.

System>Preferences>sounds results in no speaker output when test button pressed.

Is there anyway I can reload the sound drivers? Should I reinstall the whole operating system? can I run some kind of 'repair'?

Not a happy bunny.. please help.

Dell Inspiron, Ubuntu 7.10

---

### Post by BatPenguin on 2007-11-04
If Preferences -> Sound doesn't fix it (changing settings, do a test with all different options), set them to ALSA and then start playing some music file or whatever, open terminal and start up "alsamixer" (just type alsamixer in the console).

Then start going through the various mixers and see if one of them makes the sound better. Try muting them as well, and remember that sometimes the mixers don't exactly do what the claim to do. Actually, most of the time they do nothing at all =)

The safest thing (I think) is to work with one mixer at a time: so start with one slider, if it doesn't do anything, put it back to where it was, and move to the next...and try to unmute/mute each one first. Remember to have something playing so you hear the change, if any.

If this doesnt't work you could try deleting the ALSA configuration files and letting the system recreate them. I don't remember exactly what these files are (alsaconf something or other) but if this mixer thing doesn't work, try to find stuff about ALSA and how to remove/recreate configurations. There's either some alsa file in your user dir or you might wanna delete the system-wide files and just wait for the machine to recreate them at boot. You could of course just "completely remove" and reinstall ALSA through Synaptic but that usually won't help and it might have some insane dependencies (Ubuntu-desktop...) that you really might not wanna remove. Reinstalling the system...I wouldn't do that. You'll most likely have this issue later again sometime, so just try to fix it without a reinstall. If it works in Windows, then it's an ALSA issue. 

I used to have these problems that some mixer channels were getting muted every once in a while for no apparent reason (SoundBlaster Live, Edgy) and playing with alsamixer always worked. There was an optical out muted or something.

Anyway, give alsamixer a try and let us know how it goes. Hope this helps.

---

### Post by BatPenguin on 2007-11-04
OH - one more thing. Boot up from the Gutsy Live CD and see if sound works there. Just so you'll be sure that it's not a hardware problem. Sometimes Linux is pickier about broken hardware so it might be that Windows still works even if something is failing (with memory this has happened to me at least, Linux will hang with bad memory while Windows doesn't...something to do with memory use, Windows doesn't go into all memory areas as often or something).

---

### Post by thered on 2007-11-04
Thanks for that BatPenguin.  I actually thought about booting 'Live' with the CD after I shutdown last night.

Thing is I've slept on this and obviously, so has my Dell.  This morning it has resolved itself as strangely as it failed.  No crackling and normal sound and volume.

I am not so much puzzled as concerned that there is a hardware problem.  Hate these things you can't put a finger on.  Perhaps a temperature problem? I don't know..:shock:

Monitoring.

---

### Post by BatPenguin on 2007-11-04
Strange...well, glad to hear it's OK. If it was a desktop I'd suggest opening it up and dusting with pressurized air but for a notebook...I guess heating sounds likely, yeah.

Anyway, glad to hear it's OK now. Take care!

---

### Post by thered on 2007-12-03
Went off again today.  Hardware OK, works on Windoze.

Got it back on by taking playback and record off auto-detect and it came back on.

Strange - anyone any ideas?

---

