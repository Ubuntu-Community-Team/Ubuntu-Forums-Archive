---
title: "SB live! No hardware midi"
date: 2006-01-26
forum: Multimedia &amp; Video
---

### Post by barisurum on 2006-01-26
[COLOR="black"][COLOR="Green"] [SIZE="2"][COLOR="YellowGreen"][COLOR="Red"] Hello!

  I have a SB live (emu10k1) and I can use it with wave formats. But cant use the hardware midi capabilities.
 
  I installed timidity with  automatix. It created a bootup for itself (etc/init.d/timidity)
I can use it to play midi files with softsynth, but I think it eats so much system performance. So:

  1. I want to remove everything what automatix created while installing MIDI package (all programs pmidi, timidity, unison.sf2(I dont know where it is),and the scripts)

  2. I want the hardware midi to work directly with loading soundfonts via "sfxload"
  
(Note: I was using FC3 before ubuntu 5.10. There I could make hardware midi to work by following some steps:
   a) I installed alsa driver for emu10k1
   b) I think it recompiled the kernel for midi capabilities(Im not sure)
   and the emu10k1 worked with soundfonts directly (on FC3)

   Can I do it on Ubuntu too?
   I would be most happy if you could help
   Thanks[/COLOR][/COLOR][/SIZE][/COLOR][/COLOR]

---

### Post by barisurum on 2006-01-26
OK I got it working...
  I just created the devices with modprobe
   snd_emu10k1_synth etc. and wrote a script to etc/modules

---

### Post by gitfiddler on 2006-01-27
barisurum,

Could you provide more details about how you accomplished that? I'm interested in getting that working myself.

---

### Post by barisurum on 2006-01-27
Hello,

  This is how:

[COLOR="Red"]   In terminal:

sudo modprobe snd_seq_midi
sudo modprobe snd_emux_synth
sudo modprobe snd_emu10k1_synth [/COLOR](this creates the devicemodules for MIDI)

[COLOR="Red"]sudo apt-get install awesfx;asfxload
"asfxload soundfont.sf2" for ALSA or "sfxload soundfont.sf2" for OSS[/COLOR]
(and this is a tool to load soundfonts, you can find them on internet)

and after that you can play midi by selecting a port "emu10k1 : 0" etc ina midi
player

and to make these changes permanent (to load the modules at boot):

[COLOR="Red"]sudo gedit /etc/modules[/COLOR]
(Enter these lines at the end of file in editor)
[COLOR="Red"]snd_seq_midi
snd_emux_synth
snd_emu10k1_synth
[/COLOR]
save n exit. This sould work with SBLive! or Audigy (emu10k1)
Note: first you must load soundfonts to play midi...

---

