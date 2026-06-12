---
title: "no sound to sound card"
date: 2009-01-29
forum: Multimedia Software
---

### Post by anystupidname on 2009-01-29
Would somebody like to assist me in repairing sound on this system?

History:
This was originally just going to be a server (no sound packages)
I installed Ubuntu server 8.10
But then I decided later I'd install MPD and jinzora2/3 with the idea I'd be able to stream music from the net and output it to a speaker system plugged into the server's sound card.
I never got this to work (although I tried about all the wikis on MPD's site and in jinzora's forums.
I then install gnome and set up vino thinking I'd just run an app like rythmbox or something but that is where I'm at now.
I can't get any sound to the sound card...

What I've tried:
Installed and uninstalled alsa and pulseaudio several times
Tried messing with .asound file
Several random tutorials (although didn't want to try rebuilding alsa from source as one tutorial suggested)
Messed with sound parameters in gnome a lot
Messed with alsamixer in console

I feel stupid thinking about reinstalling the OS just for a sound problem...

Any assistance would be much appreciated!

---

### Post by anystupidname on 2009-04-01
I never did figure this out. I reinstalled jaunty on that box and audio out via sound card has been working fine for several months...

---

### Post by anystupidname on 2009-06-11
Well... It's back, sort of... I lost sound completely and then I tried many many things and now I've gotten it to the point where sound is weak. VERY soft, if I plug in some headphones I can barely hear it. Furthermore, the volume control doesn't work uniformly from loud to soft. I'd say from "loudest" to medium position, the volume has doesn't change and then it drops off down to off gradually from there to mute.

lspci
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Dell Device 0238
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

lsmod | grep snd
> snd_hda_intel         435636  4 
snd_intel8x0           37532  0 
snd_ac97_codec        112292  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  5 snd_hda_intel,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  18 snd_hda_intel,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  3 snd_hda_intel,snd_intel8x0,snd_pcm

I'm still on jaunty and I really am not sure what to do next...
This is a Dell Vostro 200 in case it matters.
I've tried several tutorials such as this one:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I tried blacklisting snd_hda_intel and forcing the use of another driver without success.

I tried differents parameters such as these in:
/etc/modprobe.d/alsa-base.conf
> options snd-hda-intel model=dell
options snd-hda-intel model=6stack-dell
options snd-hda-intel model=6stack
options snd-hda-intel model=dell
options snd-hda-intel model=dell-bios
options snd-hda-intel model=ref

options snd-hda-intel enable_msi=1


Any suggestions would be much appreciated!

---

