---
title: "Sound suddenly stopped working"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by EAL on 2007-05-26
Full disclosure - not much experience with Linux/Ubuntu here.

Short story:  Sound was working great until yesterday - came back from lunch, and no sound.



I installed a week ago, everything has worked fine.  My sound hardware is on the motherboard.

I can see the device in system>Pref>sounds Intel ICH5 Alsa Mixer

For sound events and music and movies, autodetect is selected.

When I hit test, nothing happens, also no audio files play, no sound with video, etc.  

I have swapped speakers, that doesn't solve the problem.

I can't put my finger on what might have caused the sound to stop working.  Yesterday I was listing to audio files, watching videos, etc.  I went to lunch, and when I came back, no sound.

I would like to try a reboot to see if that might fix it (or is that just windows talking?) but I have a 2 gig torrent file that has been downloading for days and is at 70% and I don't know how to resume it.

Anything else I can check?

Thanks

---

### Post by trak87 on 2007-05-26
How about the obvious, like a mute button is pressed or a volume slider is all the way to zero?

---

### Post by EAL on 2007-05-26
> **trak87 said:**
> How about the obvious, like a mute button is pressed or a volume slider is all the way to zero?

LOL, I tried to think of everything I'd checked.  The volume slider was the first thing I looked at.  The mute isn't on either.

---

### Post by EAL on 2007-05-26
In other words, no, the problem is not the volume or mute setting.

---

### Post by Paintcan on 2007-05-26
I am also having a similar problem. 

I can play music in banshee but sound on firefox, on any webpage or anything else just wont work. no mute button...or anything dumb like that.

---

### Post by EAL on 2007-05-26
Whup tee do!  I figured out what the problem was!

Yay me!

All I had to do was reboot Windows...err... I mean Linux. :-|

---

### Post by EAL on 2007-05-28
It just happened again.  I was just listening to MP3s maybe an hour ago.  I went to play something else just now, and the sound was dead.  The only thing I've done since it worked was post on some boards and start GAIM.

Is there a way to restart the sound without restarting the computer?  

Is there a way to run a log or something so I can see what is crashing my sound?

---

### Post by maan84 on 2007-05-28
I'm having the exact same problem, sometimes sound just stop working until I reboot which is very annoying sometimes. And when sound works and I don't play anything there's this normal buzzing sound in the headphones, but when sound doesn't work that buzz is gone (if that helps locate the prob) =)

---

### Post by EAL on 2007-05-28
Any idea what might be triggering your audio to stop working?  I have the feeling one of the programs is causing it to crash, but I thought that isn't supposed to be a problem in Linux.

I also thought you weren't supposed to have to reboot Linux to fix things.

Can someone tell me how to restart the audio system - from aslamixer it appears everything is working if I'm interpreting it correctly.

---

### Post by elfboi on 2007-12-01
Well, I had been using Edgy Eft for a while, sound was fine. Upgraded to Feisty Fawn, sound was still fine. Upgraded to Gutsy Gibbon, and sound was still fine - for a while.

Then it suddenly stopped working. Programs either tell me something like "resource is busy", or they act as if they were playing sound - but nothing can be heard. Mixer settings and volume are OK, and when I boot Windows, or Knoppix from a CD, everything is OK, so the hardware isn't broken.

I thought it might be a problem with old leftovers from Edgy or Feisty, so I just formatted the root partition and reinstalled Gutsy from scratch. First the sound seemed to work fine, but a few reboots later, it was the same as before.

If there are any specialists in here, this might help you:

root@aphrodite:~# cat /proc/asound/cards
0 [AudioPCI ]: ENS1371 - Ensoniq AudioPCI
Ensoniq AudioPCI ENS1371 at 0xec00, irq 20
1 [Bt878 ]: Bt87x - Brooktree Bt878
Brooktree Bt878 at 0xdddff000, irq 19

(I like to create a root password so that I can simply log in as root instead of using sudo for everything.)

The first device is my sound card, the second one is my TV card.

root@aphrodite:~# lsmod | grep "snd"
snd_rtctimer 4384 1 
snd_ens1371 27552 7 
gameport 17672 1 snd_ens1371
snd_ac97_codec 100772 1 snd_ens1371
ac97_bus 3456 1 snd_ac97_codec
snd_bt87x 16676 1 
snd_pcm_oss 44928 0 
snd_mixer_oss 17664 1 snd_pcm_oss
snd_pcm 80644 6 snd_ens1371,snd_ac97_codec,snd_bt87x,snd_pcm_oss
snd_seq_dummy 4740 0 
snd_seq_oss 33792 0 
snd_seq_midi 9600 0 
snd_rawmidi 25728 2 snd_ens1371,snd_seq_midi
snd_seq_midi_event 8576 2 snd_seq_oss,snd_seq_midi
snd_seq 54128 7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24324 5 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device 9228 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 55172 24 snd_ens1371,snd_ac97_codec,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_
seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 9312 1 snd
snd_page_alloc 11400 2 snd_bt87x,snd_pcm

root@aphrodite:~# aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: AudioPCI [Ensoniq AudioPCI], Gerät 0: ES1371/1 [ES1371 DAC2/ADC]
Untergeordnete Geräte: 0/1
Untergeordnetes Gerät '0: subdevice #0
Karte 0: AudioPCI [Ensoniq AudioPCI], Gerät 1: ES1371/2 [ES1371 DAC1]
Untergeordnete Geräte: 1/1
Untergeordnetes Gerät '0: subdevice #0

(I've got a German installation of Kubuntu 7.10, since German is my native tongue.)

root@aphrodite:~# lspci | grep -i audio
00:06.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 0 
00:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

(VIA-AC97-Chip is blacklisted in /etc/modprobe.d/blacklist - because I don't use integrated sound.)

root@aphrodite:~# ps -C artsd
PID TTY TIME CMD
6006 ? 00:00:29 artsd

OK, arts is running.

root@aphrodite:~# head -n 3 /proc/asound/card0/codec97#0/ac97#0-0
0-0/0: Cirrus Logic CS4297A rev 3

PCI Subsys Vendor: 0x0000

root@aphrodite:~# head -n 3 /proc/asound/card0/codec97#0/ac97#0-0+regs 
0:00 = 1990
0:02 = 0c0c
0:04 = 0404

---

### Post by smoka on 2008-01-19
Think I found out exactly what caused my sound to just disappear...

I just had a problem where my sound stopped working suddenly and I believe what happened was I had just used remote desktop connection to log on to a windows machine and got the damn annoying logon to windows sound.

Anyways, I disabled the sound on the remote machine and for some reason it seems to have actually turned off the PCM sound and volume on the machine I'm currently sitting on (Ubuntu 7.10).

I haven't tried to duplicate the problem yet, but the sound was working fine until I had disabled the sound on the remote machine (clicked on the vol icon, dragged it to the bottom and also slected mute).

The really wierd thing is that doing this seems to have done exactly the same on my local machine - luckily I noticed it early!

To re-enable on my local Ubuntu machine, I double clicked into the Volume Control Icon, and just there under Playback I found that PCM was turned all the way down to 0 and that it had been muted.

Un-muted and dragged the slider up - woohoo - all working fine :)

Just thought I'd post incase this was the cause of the issues anyone else is getting.

---

