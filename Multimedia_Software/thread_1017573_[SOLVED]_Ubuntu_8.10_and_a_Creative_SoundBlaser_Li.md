---
title: "[SOLVED] Ubuntu 8.10 and a Creative SoundBlaser Live!"
date: 2008-12-21
forum: Multimedia Software
---

### Post by sc00by on 2008-12-21
Hi,

I've got a PCI SB Live! card and haven't had any problems with it while using Debian. It worked with no intervention. Just installed Ubuntu 8.10 and it's not working at all, no sound out of it. It seems to have detected it and loaded the module but there's no sound coming out. I dual boot Windows XP and in Windows the sound is working fine so it's not a speaker/hardware issue.

Can anyone help! I'm not enjoying my first experience with Ubuntu because I switched because I thought everything would go a lot smoother but so far it has been the opposite! I have used alsaconf to turn up all the volumes and I have turned them all up/unmuted them all in the volume control gui. No dice! Any pointers anyone??

# dmesg | grep -i audigy
[   18.778862] EMU10K1_Audigy 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, high) -> IRQ 18

# lspci -v
01:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Device 0053
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at 9000 [size=32]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

# cat /proc/asound/cards
 1 [Audigy         ]: Audigy - Audigy 1 [SB0090]
                      Audigy 1 [SB0090] (rev.3, serial:0x531102) at 0x9000, irq 18

# lsmod | grep -i snd
snd_emu10k1_synth      14464  0 
snd_emux_synth         41344  1 snd_emu10k1_synth
snd_seq_virmidi        13568  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           146208  6 snd_emu10k1_synth
snd_ac97_codec        111652  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_emu10k1,snd_pcm
snd_util_mem           12416  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15236  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15232  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57776  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         15116  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  23 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd

System -> Preferences -> Sound has everything on AutoDetect except Sound Capture which is on PulseAudio Sound Server

What else could possibly be wrong!! I already had to spend a while getting grub to work, it totally set my drives up incorrectly (Error 2, then 22). Finally got that working after hacking the menu.lst but seriously considering going back to Debian if I can't crack this soon.

Many thanks!

Scooby

---

### Post by b0b138 on 2008-12-21
Did you check and make sure the volume levels are up and not muted?

---

### Post by sc00by on 2008-12-21
Hi,

yep I did, via alsaconf. Is there any other way i should try this, it seems like the most likely thing. All are unmuted and full volume in alsaconf.

"I have used alsaconf to turn up all the volumes and I have turned them all up/unmuted them all in the volume control gui. No dice!"

---

### Post by sc00by on 2008-12-21
Hi,

yep I did, via alsaconf. Is there any other way i should try this, it seems like the most likely thing. All are unmuted and full volume in alsaconf.

"I have used alsaconf to turn up all the volumes and I have turned them all up/unmuted them all in the volume control gui. No dice!"

---

### Post by b0b138 on 2008-12-21
Goto system > administration > hardware drivers and see if there is a listing there for it.  If you really have an SB live it should be working fine as thats what I have. But according to you lspci output, its an audigy.

---

### Post by sc00by on 2008-12-22
The fix was:

Open Volume Control -> Select SB device in top dropdown -> goto Switches tab -> UNCHECK Analog/Digital Output Jack -> Close

This was on by default which obviously isn't right

Thanks for the suggestions

---

### Post by HamHamT on 2009-01-02
im having a similar problem to sc00by, where i can i find "open volume control"?

---

### Post by stretz on 2009-02-05
> **sc00by said:**
> The fix was:

Open Volume Control -> Select SB device in top dropdown -> goto Switches tab -> UNCHECK Analog/Digital Output Jack -> Close

This was on by default which obviously isn't right

Thanks for the suggestions

This worked like a charm.

Thanks 4 posting the solution! Saved me some time ;)


@HamHamT: double klick the speaker icon on the taskbar

---

### Post by GARoss on 2009-02-06
> **stretz said:**
> This worked like a charm.

Thanks 4 posting the solution! Saved me some time ;)


@HamHamT: double klick the speaker icon on the taskbar

Indeed! I spent a day trying to figure this out. I assumed it was a driver issue, then the terminal said modules were missing. I had read in a Ubuntu Sound Troubleshooting Tutorial an unspecific reference to switching off the **Analog/Digital Output Jack** for those using Audigy 2 SB. In Windows, Creative has software that does mixing like this but Creative doesn't offer Linux software, so what & where was he referring to? I'm just not familiar to Ubuntu yet!
Then I read this post; "**Open Volume Control -> Select SB device in top dropdown -> goto Switches tab -> UNCHECK Analog/Digital Output Jack -> Close**". A little light went off that said to look under **Applications/Sound & Video/Gnome Alsa Mixer & UNCHECK Analog/Digital Output Jack**; found it!
Nice to have sound, isn't it?:D

Forum Administrator; could a how-to on this be posted for those who have Creative SB. A specific reference to **Applications/Sound & Video/Gnome Alsa Mixer & UNCHECK Analog/Digital Output Jack** as a solution in most cases? Word it as you like but it's a winner!

---

