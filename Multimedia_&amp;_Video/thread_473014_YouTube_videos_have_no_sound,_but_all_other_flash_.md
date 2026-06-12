---
title: "YouTube videos have no sound, but all other flash works fine. Even more peculiarities"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by SagaciousKJB on 2007-06-13
Well, I noticed this a while ago when trying to view a YouTube flash video, that it had no sound to it.  I reinstalled FireFox at this point, and it seemed to fix the sound.  However, this was a few days ago, and since then, YouTube videos are somehow unable to play sound again.

There doesn't appear to be anything wrong with alsa, as *all* of my other sound utilities work perfectly, and in fact most other flash videos work perfectly.  Even more strange, the only way that I can manage to play YouTube flash videos, is to load up Windoze XP in Vmware, and it works absolutely fine.

I have no idea what's up with this, but googl'ing and searching here, I've only managed to find some things about the alsa-oss wrapper, but I'm using Ubuntu 7.04, and I've been told that the flash players don't even use oss anymore, so it's a null point.  Whether this is true or not, even attempting to launch FireFox in the aoss wrapper, has no effect.  

Anyone have any ideas of what else I should check?

My soundcard:
```
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
```

Output of lsmod | grep snd

```
snd_emu10k1_synth       7296  0 
snd_emux_synth         34688  1 snd_emu10k1_synth
snd_seq_virmidi         6784  1 snd_emux_synth
snd_seq_midi_emul       6784  1 snd_emux_synth
snd_emu10k1           120352  5 snd_emu10k1_synth
snd_ac97_codec         97312  1 snd_emu10k1
ac97_bus                2304  1 snd_ac97_codec
snd_pcm_oss            43264  1 
snd_mixer_oss          16512  2 snd_pcm_oss
snd_pcm                76680  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9992  2 snd_emu10k1,snd_pcm
snd_util_mem            4864  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9092  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           3844  0 
snd_seq_oss            31616  0 
snd_seq_midi            8576  0 
snd_rawmidi            24448  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      7424  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                49648  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          8204  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    51716  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  3 snd
```

I'm not sure how to check the version of alsa, but it is in the newest version from my repositories on Ubuntu 7.04.  

Any ideas?

---

### Post by SagaciousKJB on 2007-06-16
Bump

Wow, you know, I keep hearing about how great ubuntu forums are for support, but 2 days on this, and not even a "Check this, " or a "Well, this might be your problem?"  Is this really that mysterious?

---

### Post by david_2001 on 2007-06-16
> **SagaciousKJB said:**
> Bump

Wow, you know, I keep hearing about how great ubuntu forums are for support, but 2 days on this, and not even a "Check this, " or a "Well, this might be your problem?"  Is this really that mysterious?
You didn't say what plugin you are using to play flash videos.  In the meantime, if you have alsa-oss installed then edit /etc/firefox/firefoxrc to read:
```
FIREFOX_DSP="aoss"
```
This is what I used to do to make Firefox sound work in Edgy and earlier versions of Ubuntu (EDIT: And check that you don't have a .firefoxrc in your home directory).  I cannot check whether it will work with Feisty because I use the X86_64 distribution and run the Windows version of flash player rather than use a wrapper to run the 32-bit Linux plugin.

---

### Post by SagaciousKJB on 2007-06-17
Adobe Flash Player 9 for Linux
Version 9.0.31.0

I uninstalled the flashplayerplugin-nonfree from apt, and installed with the installer off of the Flash website, but still no luck.  Again with the aoss, no luck.

Only place I can play YouTube videos with sound is still in VmWare.  Any other info I could give?

---

### Post by david_2001 on 2007-06-18
According to the Adobe website, "Only Advanced Linux Sound Architecture (ALSA) is supported (OSS/ESD will not play audio; audio will silently fail.)".  So it ought to just work without any alsa-oss provided that the card is correctly selected in Gnome Sound Preferences.  Googling around suggest that some have this problem and some don't and those that do don't seem to be able to find a fix that works.  Interesting that your installation worked one day and not the next - you don't by any chance have more than one sound device, e.g. motherboard sound as well as the sound card?

---

