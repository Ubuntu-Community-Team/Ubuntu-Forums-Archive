---
title: "timidity + kmid/rosegarden = only plays first note"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by kevinfishburne on 2008-04-02
I configured kmid, rosegarden, etc., to use timidity as the output device but they only play the first note/signal of a MIDI file. The note sustains until I stop the song from playing. I can play MIDI files using timidity with no problems. This question/problem has been raised a couple of times with no solution posted:

[http://ubuntuforums.org/showthread.php?t=63081&page=6](http://ubuntuforums.org/showthread.php?t=63081&page=6)
[http://groups.google.com/group/alt.os.linux.debian/browse_thread/thread/bcca980c16380aab#](http://groups.google.com/group/alt.os.linux.debian/browse_thread/thread/bcca980c16380aab#)

Any ideas? Thanks so much.

---

### Post by kevinfishburne on 2008-04-02
Initially I thought the issue was with timidity running as a daemon, since both kmid and rosegarden have the same problem. However, I got fluidsynth running using qsynth, and kmid and rosegarden still have the same problem. Timidity was no long installed or running and I specifically chose fluidsynth in their setup.

Maybe alsa is somehow responsible? I don't think the problem is with timidity/fluidsynth or with kmid/rosegarden, so I'm not sure what's left between other than alsa.

---

### Post by psych787 on 2008-07-03
In case this helps anyone, I found the solution, after struggling with the exact same issue for about a day.

When I decided to test this outside of my usual desktop session after a reboot, I noticed rtc was loosing interrupts (seen on tty1). It then occurred to me the high precision timer (HPET) may not be properly supported. After disabling this in my motherboard bios, midi works great.

Basically, disable the HPET device in your bios. If you can't, forget midi. I don't know how/if newer versions of Linux tolerate HPET - I'm using Debian Etch.

---

### Post by BDNiner on 2008-07-03
I had to disable HPET for ubuntu to install on my computer. i have not turned it on since to see if the issue was resolved.

---

