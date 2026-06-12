---
title: "Midi, Soundblaster live! and sound coming out from two speakers only"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by 'ntoni on 2006-12-23
Hi all,
I'm trying to set up my Edgy but I've got one problem that I cannot fix ](*,)
I own a Creative Sound Blaster Live! with the emu10k1 chipset, and it works well. I use it in stereo mode, and I use its multiple outs to pilot both my speakers (with the black connector) and a pair of headphones (with the green connector) at the same time. The question is, how can I hear midi songs coming out from both my speakers and my headphones?
In fact, after loading the creative soundfonts I can hear midi songs, but the midi sound comes out only from the main out, and the green jack is mute. I've tried to change the .asoundrc, but I did not manage to do anything. B.T.W. when I listen to my mp3s everything works well.
Any suggestions?
Thanks, 'ntoni

---

### Post by Unterseeboot_234 on 2006-12-29
Be sure to check out ALSA website. They had a driver. Installing the ALSA mixer and the GNOME mixer (Synaptic) along with the ALSA patch for the SB card gave me a couple more controls for sound in the Mixer. Then from one of those daily updates from Synaptic, everthing unified. I had full volume. I had front-to-back. DVD movies sounded like DVD movies. Not sure about all of the features being 100% on that great little card when it's in a linux box. I say I had most of it all working in my 32-bit box,. Made me realize how much the WIN software Creative wrote does for optimizing the SB-Live card, then I got new hardware for 64-bit. 

My 64-bit has the onboard sound chip on the PCIe video card to optimize gaming. I never fully investigated the SB-Live when I had the opportunity. But that's the fuzzy logic that worked for me.

---

### Post by 'ntoni on 2006-12-29
Thanks, I found out that gamix (used instead of the gnome mixer applet) shows many extra volume controls. Still I don't understand at all what they do. ](*,) 
I'll go check out the alsa website as you suggest and search for a detailed list of what do they do. :KS

---

### Post by 'ntoni on 2007-01-01
Bad news... I found out this graph:
[IMG]http://heim.ifi.uio.no/~haakoh/emu10k1/emu10k1-SB0100-mixer-map.png[/IMG]
showing that MIDI synth goes straight to the main out and isn't redirected to the other ones.  PCM wave does, but midi not. Software synthesis would work correctly though.

---

