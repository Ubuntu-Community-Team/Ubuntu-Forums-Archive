---
title: "sound card disappeared--not after updates"
date: 2009-12-29
forum: Multimedia Software
---

### Post by mikssilis on 2009-12-29
I've been looking into this for the last couple of days now. I turned on my Toshiba u305 laptop a while ago and the sound disappeared. I have looked at various help forums but can't seem to find a fix that will take care of this.

**lsmod**:
Module                  Size  Used by
snd_intel8x0           30168  0 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_hda_intel          26920  0 
snd_hda_codec          75708  1 snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_intel8x0,snd_ac97_codec,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

[B]aplay -l:
[/B]**** List of PLAYBACK Hardware Devices ****
ubuntu@ubuntu:~$ 

[B]lspci:
[/B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

[B]dmesg:
[/B][ 1115.663711] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1116.154001] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1116.154088] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1116.184190] hda-intel: no codecs initialized
[ 1116.184315] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1687.434347] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1687.434416] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1687.464184] hda-intel: no codecs initialized
[ 1687.464308] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 1986.292559] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 1986.292617] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 1986.324255] hda-intel: no codecs initialized
[ 1986.324379] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2224.490818] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 2224.490915] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 2904.765293] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 2905.346269] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 2905.346388] HDA Intel 0000:00:1b.0: setting latency timer to 64

[B]alsamixer:
[/B]ubuntu@ubuntu:~$ alsamixer
No mixer elems found

**/cat/proc/asound/cards:**
ubuntu@ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0640000 irq 22


Ubuntu seems to find the physical card but doesn't want to do anything with it. 
I have removed and reinstalled all alsa related things, and compiled from source, and modified the /etc/modprobe.d/alsa-base.conf, with no luck. The sound card does not show up in sound preferences or any mixer program. ](*,)

Any help would be apprecitated.

---

### Post by mikssilis on 2009-12-29
Also, same problem exists when using liveCD. It was working fine without any problems before this happened.

---

### Post by mikssilis on 2009-12-29
What that hell. I took the laptop apart to look for any signs of shorting or something like that....nothing. Put it back together, now sound works.


What the hell.

---

### Post by Brewbeck on 2009-12-31
Same thing here: On Xp Vista Win7 Ubuntu 7.10-9.10 & 5 other distros
at first sound would come back after reboot then nothing.
took her apart and fiddled with the wires connected to the Little board above the HD bay (the one with the volume nob headphone and mic jacks) booted up and sound worked.
Put the @#$%ing back together and you guessed it no sound. So I took her apart and fiddled with the wires again, YAY! sound, back together, no sound @#$%!

It has to be short or loose connection to that board but I cant find mt voltage tester.
I've done my home work, there are tons of forum posts about this all over the web (all thinking its a driver problem), Do you have a voltage tester? If so please check
it out and let me know.

---

### Post by mikssilis on 2010-01-01
Brewbeck- No I dont' have a voltage tester, i wish i did because this seems to be an indication of worse times to come. My HD also sits right on top of the sound stuff. I didn't even have to fiddle with any of the components the last couple of times this has happened, I just take out the HD and put it back in. Weird.

---

### Post by Brewbeck on 2010-01-05
mikssilis- 

"I just take out the HD and put it back in. Weird."

You must be wiggeling the offending wire just right. been there done that, sorry to say, it dosn't work any more.

I found my voltage tester. I will check the conections this weekend (the u305 is my wife's, she and it are out of town)

---

