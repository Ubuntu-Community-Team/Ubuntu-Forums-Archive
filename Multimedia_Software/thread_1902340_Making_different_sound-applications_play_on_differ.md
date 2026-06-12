---
title: "Making different sound-applications play on different ports?"
date: 2011-12-30
forum: Multimedia Software
---

### Post by isecore on 2011-12-30
I have a somewhat odd wish that I haven't been able to Google any answer to and am now posting here, hoping someone will have an idea.

I have my computer hooked up to two different outputs. One is my analog 5.1 setup on my desktop, the other is a digital output to my home cinema receiver. I switch between these depending on if I want music simply at my desk, or in the room as a whole.

Now, I'm wondering... would it be possible to make, for example, Rhythmbox output on the digital line to the receiver, while keeping all the other sounds on my "desktop" rig? So I can listen to music in the room, but notification beeps and the like get played at the desktop.

I know it's easy to assign outputs if you have multiple soundcards, but different ports on the same soundcard, is that possible?

---

### Post by lidex on 2011-12-31
> **isecore said:**
> I have a somewhat odd wish that I haven't been able to Google any answer to and am now posting here, hoping someone will have an idea.

I have my computer hooked up to two different outputs. One is my analog 5.1 setup on my desktop, the other is a digital output to my home cinema receiver. I switch between these depending on if I want music simply at my desk, or in the room as a whole.

Now, I'm wondering... would it be possible to make, for example, Rhythmbox output on the digital line to the receiver, while keeping all the other sounds on my "desktop" rig? So I can listen to music in the room, but notification beeps and the like get played at the desktop.

I know it's easy to assign outputs if you have multiple soundcards, but different ports on the same soundcard, is that possible?
I've seen this asked before and haven't seen a positive answer.

---

### Post by Lampi on 2011-12-31
I'm using kde, so this answer is kde4 related: in the sound preferences I could assign notifications to a different "card" (digital, analog, hdmi, spdif)

those are all on the same card, so maybe it works, I can't test it.

---

### Post by MoreOrLess on 2011-12-31
See if you have an alsa hw device corresponding to your digital output:
```
aplay -l
```

I can tell you that rhythmbox uses the gstreamer musicaudiosink. You can manipulate this with gconftool (or gconf-editor). The gconf key is /system/gstreamer/0.10/default/musicaudiosink

For example, I set mine to alsasink device="hw:0,1" for digital output. I'm not sure whether you can use two outputs on the same card simultaneously.

---

