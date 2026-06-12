---
title: "No sound on Breezy (386)"
date: 2005-11-25
forum: Multimedia &amp; Video
---

### Post by dcmalllory on 2005-11-25
I have an NEC Versa FXi laptop. The sound worked fine when it was running Hoary, but after reezy there is no longer any sound. The sound card is being detected (Creative Evicta EV1938). Information from "lsmod | grep snd" is :

snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm

I have checked permissions in /dev, have run alsamixer to verify the sound is not muted, and even went so far as to completely re-install both Ubuntu 5.10, and Kubuntu 5.10.

I've also dug through How-To's and the like trying to sole this.

Alas , there is only deafening silence now. It seems this is not unusual for Breezy, as there seems to be quite a few people reporting this issue.

Any help would be appreciated.

DCM

---

### Post by art2003 on 2005-11-25
run the following commands and post the output:

lsmod | grep snd
dmesg | grep snd
ls /dev/audio* -l
ls /dev/dsp* -l

---

### Post by dcmalllory on 2005-11-25
dcm@dcm-lt:~$ lsmod | grep snd
snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm

dcm@dcm-lt:~$ dmesg | grep snd

dcm@dcm-lt:~$ ls /dev/audio* -l
crw-rw----  1 root audio 14, 4 2005-11-25 06:32 /dev/audio

dcm@dcm-lt:~$ ls /dev/dsp* -l
crw-rw----  1 root audio 14, 3 2005-11-25 06:32 /dev/dsp

---

### Post by dcmalllory on 2005-11-26
For what it's worth, I spent hours on this sound issue and there is just no joy here. I finally went back to Hoary, and the sound works fine, right out of the box. Below I note what a working sound system reflects. An earlier post of mine show what some of these same items show in a non-working system.

Packages:
alsa-base = 1.0.8-4ubuntu4
alsa-utils = 1.0.8-1ubuntu1
esound = 0.2.35-2ubuntu2
esound-common = 0.2.35-2ubuntu2

Commands and output:
lspci
     0000:00:04.0 Multimedia audio controller: Creative Labs Ectiva EV1938

lsmod | grep snd

snd_ens1371            22624  2
snd_rawmidi            22944  1 snd_ens1371
snd_seq_device          8332  1 snd_rawmidi
snd_ac97_codec         64608  1 snd_ens1371
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  3 snd
snd_page_alloc          9604  1 snd_pcm
gameport                4608  1 snd_ens1371

dmesg | grep snd

(no output)

ls -l /dev/snd*

lrwxrwxrwx  1 root root  24 2005-11-26 10:35 /dev/sndstat -> /proc/asound/oss/sndstat

/dev/snd:
total 0
crw-rw----  1 root audio 116,  0 2005-11-26 10:35 controlC0
crw-rw----  1 root audio 116,  8 2005-11-26 10:35 midiC0D0
crw-rw----  1 root audio 116, 24 2005-11-26 10:35 pcmC0D0c
crw-rw----  1 root audio 116, 16 2005-11-26 10:35 pcmC0D0p
crw-rw----  1 root audio 116, 17 2005-11-26 10:35 pcmC0D1p
crw-rw----  1 root audio 116, 33 2005-11-26 10:35 timer

ls -l /dev/audio*

crw-rw----  1 root audio 14, 4 2005-11-26 10:35 /dev/audio

If the alsamixer is run, the listing of "controls" is not only greater, but in Breezy, there seemed to be no way to get all of the controls, edit the contols reliably, nor to get the same controls each time you ran the program.

Here is what alsamixer shows in Hoary.

master = on = 72<>71
master mono = muted
bass = nothing
treble= nothing
pcm = on = 71<>71
center = muted
LFE = muted
Line = muted
cd = on = 71<>71
Mic = muted
Mic Boost = muted
Video = muted
Phone = muted
PC Speaker = muted
Aux = muted

At this point I am debating whether it is worth trying to install Breezy again, but fall back to the older drivers/packages that Hoary is using.

DCM

---

### Post by jliedeka on 2005-11-26
I had a similar problem with my intel8x0 when I upgraded.  What finally worked for me was to add a file in /etc/devfs/conf.d to register my sound device.

I think the two best sources of info are the kernel docs and the ALSA project site.  If you don't have the kernel source installed, it's worthwhile to fetch it.  Look in /usr/src/linux-your.version/Documentation/sound/alsa/ALSA-Configuration.txt.  There is a lot of good info for specific cards.

My sound now works fine.  I don't have any /dev/dsp or /dev/audio files, just the stuff under /dev/snd which I think is set up by udev.  (I'm not entirely clear on how the device stuff works anymore since everyone is transitioning to udev from devfs).

Also, as a shot in the dark, see if esound is running.  If so, kill it and see if that helps.  With ALSA, you don't really need esound anymore.

---

### Post by dcmalllory on 2005-11-26
I re-installed Breezy and once again there is no sound. I did create a /dev/devfs/conf.d/alsa file to register the card as there was not a file there already; this did not help.

I notice that with the alsamixer open, there is no Master Volume, and no PCM either; this is similar to what was going on the first time I installed Breezy.

As for the kernel source, I always install this and the header files along with other items used for development.

I also went to not only the ALSA site, but the oss site as well as digging through every readme I could find.

I guess I might just downgrade the sources to see if this makes any difference.

Really a lot of effort to get sound working.

---

### Post by jliedeka on 2005-11-27
When I upgraded to Breezy, I had two other kernels from my Hoary install.  I only had sound on one of them under Hoary but none under Breezy.  That leads me to believe that something changed from Hoary to Breezy that isn't directly related to the kernel.

I find the way modules are handled to be really confusing.  There is an /etc/modutils directory and an /etc/modprobe.d which seem to be doing the same thing.  Maybe that's an artifact from upgrading.  I dunno.

---

### Post by dcmalllory on 2005-11-27
[QUOTE=jliedeka]I had a similar problem with my intel8x0 when I upgraded.  What finally worked for me was to add a file in /etc/devfs/conf.d to register my sound device.[/QUOTE]

jliedeka,

Could you post what your "alsa" file contains? I would like to see how it differs from what I did.

Thanks,

DCM

---

### Post by jliedeka on 2005-11-28
LOOKUP snd MODLOAD ACTION snd
REGISTER ^sound/.* PERMISSIONS root.audio 660
REGISTER ^snd/.* PERMISSIONS root.audio 660

---

### Post by dcmalllory on 2005-11-29
[QUOTE=jliedeka]LOOKUP snd MODLOAD ACTION snd
REGISTER ^sound/.* PERMISSIONS root.audio 660
REGISTER ^snd/.* PERMISSIONS root.audio 660[/QUOTE]

Yes, that's basically what I had. I changed the file to match the above, but still no joy.

Thanks for the post.

DCM

---

### Post by GregSnowdon on 2005-11-29
I thought I'd ad my very limited experience of Ubuntu for what it's worth. I had the same probs as you. I orgianlly installed Hoary and at first had no sound but I looked at the link posted on the forums which directed me to the "Unofficial Guide to Ubuntu..." which provides tweaks for Hoary. I did as instructed for configuring sound and got some albeit quite croaky sound.
When Breezy came along I upgraded and was struck dumb (no sound;)
I spent days trawling the forums for advice. I tried various tweaks but nothing worked. I uninstalled Breezy and re-installed Hoary and was surprised to find Hoary had also lost it's voice, despite repeating the tweaks mentioned:confused: 
I thought if I'm going to be silent I might as well have the upgraded version so I reinstalled Breezy. Still no sound. Fiddled etc....... Anyway, to cut a long story short I was messing about moving my PC's around and decided to check the other "jacks" on the rear of my soundcard, whilst trying to play a CD and to my complete astonishment there was some sound. A bit "crackly" but an improvement on silence.
I installed the various "codecs" via the "Automatix" program and I now have perfect sound.:D 
I have no idea why changing the plug from one (the original one which worked with Windows etc) to another should make any difference but it did, and the asorted installations from Automatix seems to have provided and mising "bits"
This is the link to the tweaking guide where I found Automatix, if you've already tried it I'm sorry for wasting your time. Good luck, I am pleased I perservered as I find Breezy very nice to use.
[http://doc.gwos.org/index.php/BreezyCust:D](http://doc.gwos.org/index.php/BreezyCust:D)

---

