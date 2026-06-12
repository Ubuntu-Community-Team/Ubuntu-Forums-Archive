---
title: "Teamspeak Transmits all Sound, not just Mic"
date: 2008-12-21
forum: Multimedia Software
---

### Post by 420shaggy on 2008-12-21
So I was having problems using Wine and Ventrillo (it kept on crashing) so I decided to switch to the open source linux compatible Teamspeak.  The problem I am having with it though is when I transmit sound in Teamspeak, it transmits even the sound from the games I am playing.  So currently I am forced to turn off the volume of my games when I talk in Teamspeak or else my friends get their ear drums blasted by it.  Is there a way that I can listen to my games and not transmit then in Teamspeak?

  I read in other forums that I had to turn off PCM Capture and other random things, but I tried muting everything that didn't either also mute my mic or my game, but I had no luck.  

  I am clueless, anyone know how to fix this issue?

---

### Post by 420shaggy on 2008-12-21
-bump-

Anyone have any ideas?

---

### Post by Mattventura on 2008-12-21
Open up alsamixer and press F5. What are all of the sound channels listed?

If you only get one, try doing alsamixer -c 0, alsamixer -c 1, etc until you get an error.

Also, which channel(s) says "CAPTURE" under it?

Also, what sound card are you using?

---

### Post by 420shaggy on 2008-12-23
I assume you are talking about the non-gui alsamixer, which I am not familiar with.  So I will just list the channels that I see in the gui version:

Master, Tone, Bass, Treble, 3d Control - Switch, 2d Control Sigmatel - Depth, PCM, PCM Capture, PCM, Front, PCM LFE, PCM Side, PCM Surround, Front, Surround, Center, LFE, Side, Synth, Synth Capture, Line-in, Line2, Line2 Capture, CD, Microphone, Microphone Capture, Mic Boost, Phone, IEC958 Optical, IEC958 Optical Capture, IEC958 Optical Raw, PC Speaker, Aux, Aux2, Aux2 Capture, Analog Mix, Analog Mix Capture, Audigy Analog/Digital Output Jack, Audigy CD, Audigy CD Capture, External Amplifier, HD Analog Center/LFE, HD Analog Front, HD Analog Side, HD Analog Read, HD SPDIF Center/LFE, HD SPDIF Front, HD SPDIF Rear, HD SPDIF Side, HD Channel capture, HD source Capture, Sigmatel 4-speaker stereo, Sigmatel surround Phase Inversion Playback

*Forgot to mention that my sound card is an Audigy 2 ZS Gamer*

---

