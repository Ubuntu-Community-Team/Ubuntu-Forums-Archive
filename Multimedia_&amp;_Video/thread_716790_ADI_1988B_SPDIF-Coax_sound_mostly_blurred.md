---
title: "ADI 1988B SPDIF-Coax sound mostly blurred"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by drsloth on 2008-03-06
Dear people,
i've installed Ubuntu Gutsy on my Multimedia-PC 1 week ago, it's great! (before that i had only debian on my laptop)
But my sound card does not work as expected, it's a ADI 1988B onbard, connected via SPDIF-Coax to my DD-receiver, in Win were no problems.
Unfortunately the sound is blurred nearly after every restart, that means it sounds like mp3 96kbit, but
sometimes the sound is fine.
I can not figure out, why this happens, i've read some other threads but nothing works for me.
Under System->Preferences->Audio i've choosen OSS, sometimes i can get good sound.

I've also tried the other options in this dialog:
Automatic -> no sound
AD198x Digital -> the testsound is mostly blurred, sometimes ok
AD198x Analog -> no sound
ALSA -> no sound
ESD -> not possible to get a connection to the sound server
OSS -> the testsound is mostly blurred, sometimes ok

I've figured out to get good sound, if i activate the testsound with different options, and very often opened and closed Rythmbox or Totem player , but not in a reproducible way.

Does somebody know, what to do?

The blurred sound is not because of the maximal volume. I already had fine sound with all the sound
on 100%. If it is blurred, it is blurred in every level of volume.

Something is strange, in the mixer there are two possibilies to change the volume during mp3 playback:

2:Analog Devices AD1988B (OSS Mixer) / Record running / Digital-1 (!!?Record, why that??)
0:HDA Intel (Alsa Mixer) / Playback / IEC958

all the other sliding controller do not change the volume if used. I also tried to put alle down,
to suppress background noise, but no effect.


Here are some informations, if more are needed, i'll provide them immediately.

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
2.6.22-14-generic
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 19
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xfa5ff800 irq 22
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: AD198x Analog [AD198x Analog]
  Untergeordnete Geräte: 0/1
  Untergeordnetes Gerät '0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 1: AD198x Digital [AD198x Digital]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
aplay: main:545: Fehler beim Öffnen des Audiogerätes: Device or resource busy
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
  PID TTY          TIME CMD
  PID TTY          TIME CMD
0
snd_hda_intel         337192  2
snd_seq_dummy           5380  0
snd_pcm_oss            50048  1
snd_mixer_oss          20096  2 snd_pcm_oss
snd_seq_oss            36864  0
snd_pcm                94344  3 snd_hda_intel,saa7134_alsa,snd_pcm_oss
snd_seq_midi           11008  0
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                62496  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  2 snd_pcm,snd_seq
snd_seq_device         10260  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  10 snd_hda_intel,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  3 snd
snd_page_alloc         12560  2 snd_hda_intel,snd_pcm
Codec: Analog Devices AD1988B
Address: 0
Vendor Id: 0x11d4198b
head: „/proc/asound/card0/codec97#0/ac97#0-0“ kann nicht zum Lesen geöffnet werden: No such file or directory
head: „/proc/asound/card0/codec97#0/ac97#0-0+regs“ kann nicht zum Lesen geöffnet werden: No such file or directory
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel
SAA7134
cat: /root/.asoundrc: No such file or directory
cat: /root/.asoundrc.asoundconf: No such file or directory 

```

Thanks.

---

### Post by peterdm on 2008-03-12
I'm having the exact same problem with the exact same motherboard. I've tried installing new drivers as explained [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), but in the end I had to rollback the drivers to the ubuntu defaults (the installed drivers did not work) and stuck with the module option "options snd-hda-intel model=6stack-dig". At some point I thought I had it working but now it's broken again and I don't know what happened. Anyway, if I find a solution I'll post back.

Peter

---

### Post by peterdm on 2008-03-13
Manually installing the ALSA drivers version 1.0.15 fixed the problem (as explained on [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")).
Note that these are *not* the latest drivers, 1.0.16 are out also, but they gave me other sorts of trouble.
I've searched for a backport of those drivers for 7.10 but it didn't seem to exists (yet?)...

Peter

---

### Post by scooter1556 on 2008-05-01
Hi Peterdm, i am having a similar problem to you, i have an Asus p5k premium motherboard with the ADI AD1988 codec and i want all of the sound to go to my av receiver via optical SPDIF output. I can hear the test signal when i choose either AD198x Digital or OSS but none of my applications such as totem and amarok are playing through SPDIF. How have you configured ubuntu to play through the SPDIF output?

---

### Post by peterdm on 2008-07-07
The solution is Hardy. It has updated alsa drivers. Unfortunately the sound from my apps still doesn't go through spdif automatically. I can only convince mplayer to use the spdif by specifying the appropriate command line options (-ao alsa:device=spdif).

---

