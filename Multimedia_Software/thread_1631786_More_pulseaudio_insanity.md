---
title: "More pulseaudio insanity"
date: 2010-11-27
forum: Multimedia Software
---

### Post by dewdrop_world on 2010-11-27
So, I've got rhythmbox playing and, to minimize the effect of the mic input being routed to the computer's main output, I wanted to set the main system volume to be fairly low and turn up the level in rhythmbox.

Pulseaudio won't let me do that. If I change the computer's main volume, it changes rhythm box's volume, and vice versa.

I don't think I saw that behavior before, no idea what changed.

Am I completely misunderstanding something? I thought the point of an audio server is so that the client applications could produce the signals in their own way and send them through the server. Why do they have to interfere with each other's settings?

Is there some preference to make it stop doing that? I looked in pavucontrol, device chooser and manager, don't see anything.

James

---

### Post by lidex on 2010-11-27
So you're saying when you alter the volume in RB, it changes the main volume? Mine doesn't do that. However, when you change the main volume, it will affect the volume of everything being output.

---

### Post by dewdrop_world on 2010-11-28
Of course changing the master volume will affect the volume of everything that you hear. But I'm talking about something a bit different.

- Set RB's volume to 80%. Then lower the master volume. Now RB's volume *shows 50% in the interface* - as if I touched it again with the mouse, but I never did.

- Or, set the master volume to 25%. Then raise RB's volume. Now the master volume shows up (in the slider) as 40%.

I very clearly saw that behavior yesterday. Not sure if the same thing will happen today.

James

---

### Post by lidex on 2010-11-28
Hmmm, extremely odd. Only in RB, correct? It may have something to do with the new sound panel applet, since RB controls are now integrated there.

---

### Post by dewdrop_world on 2010-11-28
Hm. Can't reproduce the issue today. The session was suspended overnight (no restart).

I also had virtualbox running - it also uses pulseaudio.

Very weird. If it happens again, I'll get screenshots (for whatever that's worth).

James

---

