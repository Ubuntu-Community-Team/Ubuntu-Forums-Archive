---
title: "After new .11 kernel upgrade, no sound"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by wocket on 2007-02-19
I upgraded my system a few days ago to the new kernel, and low and behold after restarting my system (and reinstalling my Nvidia video drivers) I noticed that my sound was globally muted, but when I unmuted it in the Gnome taskbar, I still had no sound.  I have run through the entire help file here: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
and have not been able to find anything.  My card(SoundBlaster Audigy Platinum) is detected and installed and I have unmuted everything in alsamixer, but nothing is working.  If anyone can offer suggestions, I'd be very greatful.  (Heroes will be very difficult to watch w/o sound ;)  )
Thanks.

---

### Post by wocket on 2007-02-19
here is an lsmod grep if that helps

```
$ lsmod | grep -s snd
snd_emu10k1_synth      11008  0 
snd_emux_synth         50176  1 snd_emu10k1_synth
snd_seq_virmidi        10624  1 snd_emux_synth
snd_seq_midi_emul      10112  1 snd_emux_synth
snd_emu10k1           152480  2 snd_emu10k1_synth
snd_ac97_codec        127064  1 snd_emu10k1
snd_ac97_bus            4352  1 snd_ac97_codec
snd_util_mem            7552  2 snd_emux_synth,snd_emu10k1
snd_hwdep              14088  2 snd_emux_synth,snd_emu10k1
snd_pcm_oss            57344  0 
snd_pcm               108168  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         13200  2 snd_emu10k1,snd_pcm
snd_mixer_oss          22784  1 snd_pcm_oss
snd_seq_dummy           6020  0 
snd_seq_oss            45824  0 
snd_seq_midi           12160  0 
snd_rawmidi            34432  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     11520  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                77344  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              31112  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         12180  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79016  15 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14112  1 snd

```

---

### Post by Algoritm on 2007-02-19
I have the same problem. Sound worked before, but not now. I've tried everything. Hope someone finds the solution. 

I have Soundblaster Audigy 2 ZS

---

### Post by wocket on 2007-02-19
me too.  I'm getting more and more tempted to blow ubuntu away and start over, but I'm worried about doing all of that and then hitting this problem again.

---

### Post by briguy on 2007-02-19
I have the same problem - rebooted with the .10 kernel and sound is back again.  Boo-urnes!

---

### Post by Protoss on 2007-02-19
Just downgrade to the .10 kernel, easiest way out of it. For some reason .11 had SMP enabled for me, which my rt61 drivers hate, so it kept locking up, .10 works perfectly for me.

---

### Post by wocket on 2007-02-19
well, that is what I thought, but I am running the .10 and it's still no use?  Am I just screwed now? (I cannot think of anything else that I did except for upgrade the kernel)  Is there a way to actually 'downgrade' as in reinstalling all the .10 modules etc?

---

### Post by wocket on 2007-02-20
Thank you for your suggestions. I'm going to keep trying different things.  If all else fails, I'll reinstall on Wednesday.

---

### Post by tmd47762 on 2007-02-26
I've had the same problem with the .8 generic upgrade for Feisty.  When running the test sounds ALSA, OSS, and Autodetect don't work.  I get a test sound for multichannel playback, but so far I can't get any of my audio players to use that output.  I have 2 SoundblasterLive! Cards and both appear to behave the same way, yet they both detect just fine.

---

### Post by tmd47762 on 2007-02-26
I have solved my problem and hopefully this may help anyone else who is having the same problem.  Turns out the first thing I thought of was the right answer in the end once I figured out how to do it.  

Essentially it's like reinstalling, but only for the sound modules to get them to fit with your new kernel.  The full guide is here: [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#General_Help]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#General_Help")

The symptoms are your card is detected, but no sound comes out, and the solution is to type 
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

This removes the problem sound configuration, but also removes gdm and ubuntu-desktop (or ubuntu-minimal in Feisty).  In general, take note of anything it is going to remove, write it down so that you can reinstall it, because these are very important things.  Then you simply type in:
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-minimal 

Include any other programs it decided to uninstall in this list as well.  Go through this and restart the computer and it should work.  Also at this point make sure you haven't mistakenly moved your plugs around.  I thought it had failed at first, but the problem was having moved my speaker jack to my second sound card.

---

### Post by bracc0 on 2007-03-08
I have uninstalled alsa driver 1.10.12 on my laptop.
I installed ver. 1.10.14rc2 with no problems. I ran modprobe snd-hda-intel, no errors.

Now when I reinstall all packages that I had to uninstall with old alsa driver (gdm, gnome-applets, etc.) the apt-get program re-installs automatically alsa stuff ver. 1.10.12.

Anyone has any idea about how to force the installation of alsa driver 1.10.14rc2?

Thanks
Claudio

---

