---
title: "ES1371 sound not working"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by sglow on 2007-04-20
I'm reposting this from the general install list.

----

I have recently installed Feisty on a PC with an on-board Ensoniq ES1371 sound card. I'm not getting any sound at all.  The PC in question is a few years old.  It's a Micron PC with an 866 MHz processor and 256 Meg of RAM.  Not sure exactly what year I got it, but I'd guess it was around 2000 - 2002.

I've tried booting from the 6.10 install CD, and sound works there. No sound booting from the 7.04 install CD however.

The chipset is detected. lspci gives me:

00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)

The driver seems to be getting loaded properly. In lsmod I see:

...
snd_ens1371 27552 1
gameport 16520 1 snd_ens1371
snd_ac97_codec 98336 1 snd_ens1371
ac97_bus 3200 1 snd_ac97_codec
snd_pcm_oss 44544 0
snd_mixer_oss 17408 1 snd_pcm_oss
snd_pcm 79876 3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 4740 0
snd_seq_oss 32896 0
snd_seq_midi 9600 0
snd_rawmidi 25472 2 snd_ens1371,snd_seq_midi
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi
snd_seq 52592 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_mid i_event
snd_timer 23684 2 snd_pcm,snd_seq
snd_seq_device 9100 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi ,snd_seq
...

I see /dev/dsp. This is owned by root with group audio. Access mode is 660.

I'm in the audio group. Also tried changing mode to 666 and trying as root. Still no joy.

I've checked the alsamixer and turned every channel on and up.

I've looked through dmesg and logs. Nothing that looks interesting to me there.

The sound preferences tool may be interesting though:

I have a 'Default Mixer Tracks' selection at the bottom of this that I don't see on another computer running ubuntu (6.10). This gives me two mixer choices: 'Ensoniq AudioPCI (Alsa mixer)' and '0x43004e53 C?N,0x43004e53 C?N (OSS Mixer)'.

Regardless of which mixer I select, I see the same set of choices in the 'Sound playback' drop down box. The choices are:
Autodetect
ES1371 DAC1
ES1371 DAC2/ADC
ALSA
ESD
OSS

No matter which of these I select, I get the same result when I hit the test button. The testing pipeline dialog pops up, and the progress bar just sits in the first location. There is no motion on the progress bar and no sound. I can hit OK to get rid of the progress bar, but something is clearly hanging when the system tries to produce sound.

I've been through the sound guide and browsed the forums, but nothing seems to have helped.  I'm actually a pretty experienced Linux user (just switched from Gentoo which I've used as my only OS for a couple years).  Coming up short on this problem though.

Any thoughts?

Thanks,
Steve

---

