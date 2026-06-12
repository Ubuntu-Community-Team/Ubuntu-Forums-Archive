---
title: "Audacity recording line-out"
date: 2009-03-06
forum: Multimedia Software
---

### Post by Crow_ on 2009-03-06
I'm running Ubuntu 8.10 on Gnome, and I'm recording using a Peavey mixer via the line-in.

My sound card is a Creative Labs SB-XFI, which is probably the problem.

In my volume control, I muted my Microphone-Capture and unmute the Line-In-Capture, which I assume makes me record the Line-In.

Anyway, I recorded my electronic drums as the first track in Audacity fine - that's not the issue. However, when I went to record my second track, it recorded the drum track on top of the new track (So if I mute the drum track I still hear the drums in the new track basically). Audacity seems to be recording both my inbound and my outbound simultaneously.

What can I do to fix this? In my Audacity preferences I have both input and output set to "ALSA: Creative X-Fi: WaveOut/WaveIn (hw:0,0)". This is more or less the same option I used in Windows for Audacity recordings when I switched over, but I never had this problem.

---

### Post by ilioscio on 2009-03-06
have you tried disabling overdub? found in Edit > Preferences > Playthrough

---

### Post by Crow_ on 2009-03-07
I have "Play other tracks while recording new one" checked because otherwise I would have no submaster to go off of, but the "Play new track while it's recording" box is unchecked.

Also, if I mute my Line-In in my regular Ubuntu Volume Control, it also mutes the Line-In Capture, so I can't fix the problem via headphones either.

Right now my solution is to have the sound come out of my USB headset, and then I turn my speakers off, but that's kind of annoying :/

---

