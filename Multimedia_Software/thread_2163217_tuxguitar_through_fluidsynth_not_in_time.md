---
title: "tuxguitar through fluidsynth not in time"
date: 2013-07-17
forum: Multimedia Software
---

### Post by xandermann on 2013-07-17
I have tuxguitar hooked up through qsynth so I can connect it to Ardour through jack.

The thing is when I record tuxguitar set at 120bpm on a ardour project set up for 120bpm the recording (after being trimmed and lined up) starts off for the first few beats on beat but by the end is about a half beat off.

I want to add a drum track from hydrogen (which does come in correctly on beat).

Thanks for any help.

---

### Post by xandermann on 2013-07-17
I used a work around to fix the problem.  Turned jack off and quit all programs. Exported the tuxguitar file as a midi and then used: fluidsynth -F out.wav /usr/share/sounds/sf2/FluidR3_GM.sf2 myfile.mid to turn the mid into a wav which I imported into Ardour.  So I can add my drum track now, but if anyone knows how to do it with the setup I had running or to just explain the issue so I understand what happened I'd appreciate it.

---

