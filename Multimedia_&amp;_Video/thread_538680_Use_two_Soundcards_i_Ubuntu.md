---
title: "Use two Soundcards i Ubuntu"
date: 2007-08-30
forum: Multimedia &amp; Video
---

### Post by deloco on 2007-08-30
Hi everybody, I use Ubunto for about six months now and I am very Happy with it. There's only one little thing that drives me nuts...

I have two SOundcards installed, one on-Board Soundchip (VIA) and on professional Audicard (M-Audio). Both work fine, but it seems that Ubuntu randomly decides which soundcard is the first (hw:0) and which is the second (hw:2).

I have the onboard-card connected to a headset for Audioceonferenceing and the M-Audio-Card is connected to a big Mixer for Music...

The problem is, that only every second time I boot up my system the M-Audio-Card is the first audiodevice, so Amarok (or any other app), which is set to use hw:0 as output device, plays back music through this card (and therefore I get sound at the MIxer/Amp).
But every other second time the internal soundchip is set to hw:0 and Amarok plays through the headset...

It's really annoyng, that I have to check the output every time!

Can someone help me with this?
How do I set up the Sounddevices so that they always are the same in the system?
By the way, this happens in Ubuntu (Feisty) and UbuntuStudio.

Greetz,
deloco

---

### Post by OoooMatron on 2007-08-30
have you tried setting up the devices in the audio control panel? it allows you to prioritise what sound card to use for what reason.

i use 2 sound cards (1 for skype and 1 for general use) and i don't ahve any problems.

---

### Post by deloco on 2007-08-31
Oh well.. I forgot to metion that I'm using KDE and therefore don't have the audio-config...
But anyway, the problem doen't get solved by it anyway... 
You see, Ubuntu recognizes which soundcard is which, so it routes the sound to the correct card, but when you use an app that has it's own audiocard-config this doen't work. AmaroK thinks it sends the card to the same soundcard as always, but it sends it sound to device hw:0, and Ubuntu switches hw:0 ftom one card to another... 
Same goes for Jack, which I need for music-production...

---

### Post by Jorit on 2007-09-01
I feel your pain deloco, fortunately I just finished fighting my way through a very similar issue (on my way to another).  As I understand it, you have two options, the preferred is that you should be able to use the driver returned device name to specify what sound hardware to use, in my case:
```
$ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1370/1 [ES1370 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1370/2 [ES1370 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```
my system shows both AudioPCI and CK8S cards are available so I should be able to run
```
$ alsaplayer -o alsa -d CK8S startup.wav
```
according to [http://alsa.opensrc.org/index.php/MultipleCards#Recommended_solution]("http://alsa.opensrc.org/index.php/MultipleCards#Recommended_solution")
Unfortunately, this results in "Unknown PCM CK8S" when I try it so I ended up using the old solution of forcing module load order.  While I'm not certain that this is the technically correct file to edit, it does work, simply add these lines to the end of you /etc/modprobe.d/alsa-base file (modified for your system of course)
```

options snd-intel8x0 index=0
options snd-ens1370 index=1

```
and of course, since we're dealing with kernel module loading, you'll need to reboot. Hope this helps

---

### Post by deloco on 2007-09-01
Thanks for that hint... I'll do that just when I'm on my home-PC... I'm at my girlfriends machine right now and have to stay all night...
Tomorrow I'll try your way. Would be very good, It begins to really piss me off....
deLoco

---

### Post by deloco on 2007-09-02
Hmm.... Now I have the problem what I have to write in that file... 
What are my Souindcards?

I have an OnBorad VIA 8235 and an M-Audio Delta44 withe an ICE1712 Chip... How do I find out what modules they need?


I'll just try 
option snd-ice1714 index=0
option snd-via8235 index=1

Maybe it works...

---

### Post by deloco on 2007-09-03
Hm... Now my onbrad card doesn't seem to work at all, but my Delta44 (ICE1714) works now as first device...
Strange... I'll try something different...

---

### Post by Jorit on 2007-09-04
After a look at the alsa modules list, i think the driver you need for your integrated audio should be "snd-via82xx" but a sure way to check what modules are being loaded is the file /proc/asound/modules though you may have to reverse the earlier change to the alsa-base file and reboot to ensure all modules load cleanly.

---

### Post by malrost on 2007-09-04
deloco --

Check this thread: [http://ubuntuforums.org/showthread.php?t=91948]("http://ubuntuforums.org/showthread.php?t=91948")

This thread is actually the source for the book "Ubuntu Hacks" Hack #83, "Mount Removable Devices with Persistent Names".) Though it's dealing with drive assignments, I believe you may be able to apply this technique to sound cards as well.

You can also find the text of Hack #83 by googling the title (such as here: [http://codeidol.com/unix/ubuntu/Administration/Mount-Removable-Devices-with-Persistent-Names/]("http://codeidol.com/unix/ubuntu/Administration/Mount-Removable-Devices-with-Persistent-Names/")

An excerpt

*"...but there's a major annoyance associated with them. When I reboot Ubuntu (a rare occasion, to be sure, but it does happen), their mount points shift around. Sometimes FireWire drive number one gets /media/sdb1, and sometimes /media/sdc1. The same thing happens to the other drives as well, which wreaks havoc with my backup scripts...*

---

### Post by deloco on 2007-09-06
Thanks for that link, but as far as I understand that tutorial I really don't see how I could use that for my Audiodevices... It seems to be very specifically for harddrives....

---

