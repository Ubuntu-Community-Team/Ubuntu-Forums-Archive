---
title: "Delay with midi sounds"
date: 2009-01-19
forum: Multimedia Software
---

### Post by daoo on 2009-01-19
I'm trying to use tuxguitar and [Virtual MIDI Piano Keyboard]("http://vmpk.sourceforge.net/"). VMPK is for using with my midi-keyboard. For this to work I've installed timidity++ with apt and start the daemon with the init.d script. But when vmpk or tuxguitar is trying to play a note, there's always a slight delay, 0.5-1 sec, which isn't very nice. When playing an entire track in tuxguitar the notes are played at the wrong time.

However when playing a midi file with the timidity command, banshee or totem, the playback is perfect.

I'm using Jaunty 64-bit but had the the same problem in Interpid 64-bit. I have a Creative Audigy LS (SE) if that helps.

I've tried by uncommenting lines in /etc/timidity.cfg but it didn't do any difference.

If anyone could help me I would be grateful.

---

### Post by DonnieP on 2009-01-20
> **daoo said:**
> I'm trying to use tuxguitar and [Virtual MIDI Piano Keyboard]("http://vmpk.sourceforge.net/"). VMPK is for using with my midi-keyboard. For this to work I've installed timidity++ with apt and start the daemon with the init.d script. But when vmpk or tuxguitar is trying to play a note, there's always a slight delay, 0.5-1 sec, which isn't very nice. When playing an entire track in tuxguitar the notes are played at the wrong time.

However when playing a midi file with the timidity command, banshee or totem, the playback is perfect.

I'm using Jaunty 64-bit but had the the same problem in Interpid 64-bit. I have a Creative Audigy LS (SE) if that helps.

I've tried by uncommenting lines in /etc/timidity.cfg but it didn't do any difference.

If anyone could help me I would be grateful.

Try using fluidsynth instead of timidity.  You'll need the fluidsynth, fluid-soundfont-gm and qjackctl packages.

---

### Post by daoo on 2009-01-20
I installed fluidsynth with the soundfonts, but I don't understand how to use qjackctl. If i run: "fluidsynth -m alsa_seq /usr/share/sounds/sf2/FluidR3_GM.sf2", I get a new connection which has terribly bad sound quality (without delay tough).

---

### Post by DonnieP on 2009-01-20
> **daoo said:**
> I installed fluidsynth with the soundfonts, but I don't understand how to use qjackctl. If i run: "fluidsynth -m alsa_seq /usr/share/sounds/sf2/FluidR3_GM.sf2", I get a new connection which has terribly bad sound quality (without delay tough).

First run JACK Control (qjackctl) from the Applications menu but don't turn the server on.  Then run fluidsynth without the '-m alsa_seq' parameter.  Then go back to JACK, click the connect button and connect the keyboard (or whatever else) on the left side to 'FLUID Synth' on the right side.  Sound quality might be affected by the gain setting vs system volume.

---

### Post by daoo on 2009-01-22
This works well for VMPK, but not with tuxguitar.
Tuxguitar doesn't appear like vmpk in the connections manager of qjackctl and when selecting the midiport with tuxguitar's settings->sound it gives the same bad quality as before.

PulseAudio volume according to alsamixer is 78

Typing "settings" in fluidsynth gives:
```

audio.output-channels    2
audio.periods            16
audio.alsa.device        default
audio.file.name          fluidsynth.raw
audio.sample-format      16bits
audio.period-size        64
audio.jack.autoconnect   0
audio.jack.multi         no
audio.jack.id            fluidsynth
audio.oss.device         /dev/dsp
audio.input-channels     0
audio.driver             alsa
midi.alsa.device         default
midi.alsa_seq.device     default
midi.alsa_seq.id         pid
midi.oss.device          /dev/midi
midi.driver              alsa_seq
synth.reverb.active      yes
synth.ladspa.active      no
synth.midi-channels      16
synth.polyphony          256
synth.sample-rate        44100.000
synth.verbose            no
synth.chorus.active      yes
synth.effects-channels   2
synth.gain               0.200
synth.audio-channels     1
synth.dump               no
synth.audio-groups       1
shell.prompt             > 
shell.port               9800
lash.enable              0

```

---

### Post by DonnieP on 2009-01-24
Have you installed tuxguitar-alsa and tuxguitar-fluidsynth?

---

### Post by daoo on 2009-01-24
Yes, but the sound quality doesn't change from what I can tell, it's still bad. I've also tried installing tuxguitar-jse and using the Real Time Sequencer instead of TuxGuitar sequencer, still no difference.

EDIT: This maybe linked to something else, because I just noticed that I get some crunching with all sound playback. Though it's not the same amount for all applications. For Banshee there's almost impossible to hear it, but with the flashplayer and youtube you'll definitively hear it and in tuxguitar it makes your ears hurt.

---

