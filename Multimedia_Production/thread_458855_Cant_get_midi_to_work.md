---
title: "Cant get midi to work"
date: 2007-05-30
forum: Multimedia Production
---

### Post by SickNick on 2007-05-30
I use ubuntu studio on my desktop i love the operating system, but i have no clue on how to get midi to work. For example when i use Wired, i have my Jack Connection Kit started nd it detects my USB MIDI keyboard. I goto settings check off my midi keyboard, i then open a midi track, select my midi keyboard as a input and i select the output as one of the synths, i goto play something, and nothing shows up or is heard, i hit the keys and the virtual keyboard on the synth dosent do anything it shows no midi signals, can anyone help me out with this?

---

### Post by kayosiii on 2007-05-31
I am not sure that Midi is fully implemented in the version of Wired that shipped with Ubuntu studio.  Try getting sound working with zynaddsubfx first...

---

### Post by SickNick on 2007-06-01
I just tried that synth, i was able to get sound by clickin the keys and so on i eventually messed it up, whenever i played something on the midi keyboard there was no signal to the program, at least there i never connected ne midi, the other programs seemed logically correct

---

### Post by Sandsound on 2007-06-02
> **SickNick said:**
> whenever i played something on the midi keyboard there was no signal to the program, at least there i never connected ne midi, the other programs seemed logically correct

Try to open the panel window in ZynAddSubFX. Maybe your keyboard only sends midi on a single port, and assuming you have connected it properly in jack, you should be able to identify what channel recieves the signal in ZynAddSubFX when you hit a key.

And yes... no midi in Wired :-(
I use Rosegarden, it's not so cool-looking like Wired, but at least it works :-)

---

