---
title: "Soundfonts and Audigy external"
date: 2007-10-15
forum: Multimedia Production
---

### Post by Tigera on 2007-10-15
I posted this earlier in Multimedia/Video and didn't get a response, so I apologize in advance for the double-post.
I don't know if the Creative Soundblaster Audigy external USB has a 0404 chip in it either, so if it does, I've triple posted, shame on me.
Sound works fine on my external USB Audigy (this is my second card, mind you), but I can't get asfxload to load a soundfont for it.  I'm running this:

asfxload --hwdep hw:1,0 4GMGSMT.SF2

and it tells me this:

No Emux synth hwdep device is found

Can anyone help me fix this?

---

### Post by Unterseeboot_234 on 2007-10-18
The ONLY way I have had satisfactory results with:
1. MIDI
2. SoftSynth
3. Software
4. Linux

is to use java's JMF libraries and it does play wonderfully through the Creative Live and Audigy hardware and other sound cards supported by JRE. Starting up a gneric LInux SoftSynth-server or some other dameon servers all overloads my hardware -- Muse and Rosegarden lock up my machine.

Linux, if it does MIDI, uses external hardware. Java can MIDI with your choice of SoundFonts but it takes you to write your own software. 

And then there is:
[**Creative Labs. open source**]("http://opensource.creative.com/")

The project is for 64-bit X-Fi. It may be what I have been looking for to author MIDI in a graphics tool.

---

### Post by Tigera on 2007-10-22
Thanks for the reply - I would not be against using Java to compose music, but do you know of any good composition or sequencing programs?

---

### Post by Rexbron! on 2007-10-23
Rosegarden for midi sequencing and scoreing. Hydrogen for a drum machine.

---

