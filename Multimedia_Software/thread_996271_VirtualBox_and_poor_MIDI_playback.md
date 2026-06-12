---
title: "VirtualBox and poor MIDI playback"
date: 2008-11-28
forum: Multimedia Software
---

### Post by djbon2112 on 2008-11-28
I'm using VirtualBox to virtualize a Windows XP environment so I can use Sibelius 4 for music composition. However, the playback is extremely erratic and choppy (demonstration [here]("http://www.youtube.com/watch?v=J9I3_lziLk0")). I'm using Ubuntu Studio 8.10 with the RT kernel (which ironically makes the issue worse, generic plays better), the latest VirtualBox OSE from the repos, and both PulseAudio and ALSA (tried both, ALSA is the better of the two) for sound. Anyone have any ideas as to the cause, or a solution?

---

### Post by demios on 2008-12-14
k, I'm no pro, but I'm also running Ubuntu studio 8.10, and the rt kernel doesn't work yet, which is why your audio playback was crap with it on. but they're working on it, apparently.

also, this guy ([http://forums.virtualbox.org/viewtopic.php?p=26055&sid=edb5d4f020fc7dd19e2b11bcd8589eaf](http://forums.virtualbox.org/viewtopic.php?p=26055&sid=edb5d4f020fc7dd19e2b11bcd8589eaf)) had the same problem as you, and got it solved by using "PUEL" instead of "OSE" -- I'm still researching to try this thing out, as WINE isn't being friendly to sibelius for me, so I don't really know virtualbox.

hope that helps.

---

### Post by networm1230 on 2008-12-14
> **demios said:**
> k, I'm no pro, but I'm also running Ubuntu studio 8.10, and the rt kernel doesn't work yet, which is why your audio playback was crap with it on. but they're working on it, apparently.

also, this guy ([http://forums.virtualbox.org/viewtopic.php?p=26055&sid=edb5d4f020fc7dd19e2b11bcd8589eaf](http://forums.virtualbox.org/viewtopic.php?p=26055&sid=edb5d4f020fc7dd19e2b11bcd8589eaf)) had the same problem as you, and got it solved by using "PUEL" instead of "OSE" -- I'm still researching to try this thing out, as WINE isn't being friendly to sibelius for me, so I don't really know virtualbox.

hope that helps.

I have Virtual Box installed on my pc i am running opensuse OS 10.3 down lode oss (open sound system) at [http://www.opensound.com/oss.html](http://www.opensound.com/oss.html)

hop this helps

---

