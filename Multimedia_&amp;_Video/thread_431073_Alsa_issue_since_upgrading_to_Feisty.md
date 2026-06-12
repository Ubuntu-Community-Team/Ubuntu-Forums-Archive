---
title: "Alsa issue since upgrading to Feisty"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by raskolnik on 2007-05-02
I'm having some trouble getting my sound working properly since upgrading to feisty. I know a lot of people are having similar issues, judging from the forums, but I haven't found a solution to my problem yet in their posts.

The problem is this: I can't get two or more applications to use sound at once. All programs are set to use alsa as the output. Sound works fine in the first program run, but no others.

I have an onboard intel card, and a pci sound blaster live (value) card. When I first installed, sound would only come out of the onboard card, regardless of what I set the default card to in gnome sound preferences (system->preferences->sound), but I've solved that by blacklisting the snd_intel8x0 module. Now &#8220;SBLive! Value [CT4670] (Alsa Mixer)&#8221; and &#8220;TriTech TR28602 (OSS Mixer)&#8221; are the only cards listed, and audio is playing from the sound blaster.

I've followed the feisty wiki on setting up gnome, alsa and esd ([http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty))...but this hasn't changed anything.

Here's some output that might be helpful...

asoundconf list

```
Names of available sound cards:
Live
```


lsmod | grep snd

```
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  1 snd_emu10k1_synth
snd_ac97_codec         98336  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
```


Does anyone have any idea what's going wrong, and maybe how to fix it? I'd really appreciate any help with this. Thanks...

---

### Post by mattigras on 2007-05-03
I'm having problems with  sound in Feisty  as well.  I originally had Edgy installed and sound worked fine, then i upgraded to feisty using the update manager and sound worked fine. then I nuked it and did a fresh install of feisty from the desktop-i386 CD and now my sound doesn't work at all.  My lsmod|grep snd is virtually the same as yours, but my box has no onboard audio and my card is an SB Audigy, although I have the same chip as you (TR28602).  

Come to think of it, I installed Feisty on my laptop from the same CD and sound didn't work either.  I thought it was a problem with the Intel ICH7 chip, but I'm beginning to see a pattern here.  I think I'll download and burn the ISO again then do a reinstall to see if my original was corrupted. If that doesn't work, i'll try installing from the edgy CD and upgrading again (that'll take forever...). meanwhile, here's some info... 

 lsmod|grep snd:
```
snd_emu10k1_synth       8192  0 
snd_emux_synth         35456  1 snd_emu10k1_synth
snd_seq_virmidi         7936  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_emu10k1           121248  2 snd_emu10k1_synth
snd_ac97_codec         98336  1 snd_emu10k1
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10888  2 snd_emu10k1,snd_pcm
snd_util_mem            5760  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9988  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8448  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                52592  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9100  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd

```

lspci:
```
02:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

```

**EDIT:**[COLOR="Blue"]I solved this by unchecking the "Audigy Analog/Digital Output Jack" switch in alsamixer. Sound works fine now, but is laggy and has feedback using JACK, but that's another story,[/COLOR]

---

### Post by henriquemaia on 2007-05-03
Hi,

I have upgraded my girlfriend&#8217;s computer and she was using Dapper, where sound worked fine. Now that I have done a clean install of Feisty, I have no sound at all. Any ideas on how to fix this?

** EDIT:**[COLOR=Blue] This is solved. I burned another Feisty CD and made a clean isntall. That did the trick.[/COLOR]

---

### Post by raskolnik on 2007-05-11
I've found changing all output to OSS gives me proper mixing from all programs...So Alsa locks the audio when used, and OSS allows multiple programs to play sound simultaneously. Isn't that the reverse of what should be happening? Is this related to Gnome disregarding my sound card selection in System->Settings->Sound? This also occurs when booting from the Feisty LiveCD. Edgy worked fine.

I'm glad it's working, but this can't be right. Does anyone have any information on this, or be able to point me towards something that does? Anything at all would be appreciated. If more info on my system is needed, I'll be glad to provide it. Thanks.

---

### Post by merlin114 on 2007-09-05
I was running Dapper and had no sound issues.  But with both the Fiesty Live CD and the clean install of Feisty, I'm having a similar problem as you guys.  I have an older Gateway PC with SB Live, and now I get nothing but static -- constantly.  My asoundconf lst also shows "Live" as the detected card.  I messed with the ALSA mixer a bit, but nothing changed -- same constant static.  When I boot to Dapper on my other drive, sound still works perfectly.  I briefly loaded the Gutsy Tribe 5 Live CD and had the same sound problem.

Any help would be most welcome.

---

### Post by merlin114 on 2007-09-05
For those having poor quality or no sound with SB Live sound card, here is what worked for me.  From the terminal I opened 'alsamixer' which gives a GUI full of sliders.  Messing with a few didn't do it.  But per someones suggestion (from where, I can't recall), I started putting them all to zero.  As I went, I discovered that there are alot more sliders off to the right if you keep scrolling.  When I got to the IEC958 sliders and muted them, the crackling static suddently went away.  I also muted the PC Speaker and set AC97 to 0.  Then I put in a CD to provide some sound and started adjusting the sliders.  I pretty much set all the others to 74, unmuted the Tone, PCM, Line, CD, and External sliders, and then set Bass at 65 and Tone at 75.  Everything sounds beautiful now.  Hope this helps.

---

