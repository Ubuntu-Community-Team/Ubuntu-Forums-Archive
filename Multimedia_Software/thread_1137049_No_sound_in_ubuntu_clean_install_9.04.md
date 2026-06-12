---
title: "No sound in ubuntu clean install 9.04"
date: 2009-04-25
forum: Multimedia Software
---

### Post by gmorphis on 2009-04-25
Not sure if my sound issue is related to the other posts or bugs..
Clean install of ubuntu 9.04 on a HP dt4v. 
Installed PulseAudio apps.
Applications -> Sound & Video -> PulseAudio Volume Control 
I have Null Output in the Output Devices tab. 
I'm getting no sound anywhere. The first 2 times I booted I had some weird congo drum that lasted a while before fading off. I didn't test playing sounds so I don't know if sounds worked at all minus those annoying beats. It was so annoying I had to mute the audio. When I un-muted the audio I hear nothing. 
lspci shows : 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

aplay -l shows : 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

alsamixer shows :
Master 51
Headphon 68<>68
PCM 62<>62
Front 68<>68

Anyone have any ideas to test? I really want to use Linux full-time as this release is beautiful! I just need the sound to work :confused:

---

### Post by Gforce20 on 2009-04-25
I'm having a very similar problem, with the same sound card but on a Dell E520. I've been looking for solutions for two days, and nothing has come up yet.

---

### Post by eatayeh on 2009-04-25
Hey i was facing a similar problem and the following solved it:


sudo apt-get install linux-backports-modules-jaunty

Restart your system...

let me know if this fixes your problem

---

### Post by Gforce20 on 2009-04-25
> **eatayeh said:**
> Hey i was facing a similar problem and the following solved it:


sudo apt-get install linux-backports-modules-jaunty

Restart your system...

let me know if this fixes your problem
I already installed that, and still have no sound.

---

### Post by eatayeh on 2009-04-25
Did you also add at the end of /etc/modprobe.d/alsa-base the following line?

options snd-hda-intel model=hp


if not, do it and then restart again...

---

### Post by Gforce20 on 2009-04-25
> **eatayeh said:**
> Did you also add at the end of /etc/modprobe.d/alsa-base the following line?

options snd-hda-intel model=hp


if not, do it and then restart again...
I've added "options snd-hda-intel model=dell" to the end, since it's a dell computer. I've tried multiple other models, and none of them were any better.

---

### Post by eatayeh on 2009-04-25
Have you tried to boot from the Live CD and test the sound there?

---

### Post by rcastberg on 2009-04-25
I have similar problems with a dell e6400, and just rebooted into the previous kernel 2.6.27-11 and here my sound works find.

So i might be tempted to use this kernel.

Rene

---

### Post by Gforce20 on 2009-04-25
> **eatayeh said:**
> Have you tried to boot from the Live CD and test the sound there?
I just tried that, and still heard no sound.

---

### Post by gmorphis on 2009-04-26
I uninstalled 64-bit version, reinstalled 32-bit version, still no sounds.. just the annoying conga beats. I tried all the steps listed here and even installed pulseaudio 9.15 via PPA still no sound. 
Volume Control still shows "Null Output" in Output Devices

---

### Post by smileypaul on 2009-04-26
Same issue.. 

32 bit Ubuntu.. I can hear the congo sound upon startup.. but no sound thereafter:(

same Intel HDA

---

### Post by Gforce20 on 2009-04-26
> **gmorphis said:**
> I uninstalled 64-bit version, reinstalled 32-bit version, still no sounds.. just the annoying conga beats. I tried all the steps listed here and even installed pulseaudio 9.15 via PPA still no sound. 
Volume Control still shows "Null Output" in Output Devices
The way I solved the "Null Output" issue was adding "options snd-hda-intel model=hp" to the end of /etc/modprobe.d/alsa-base.conf (I needed model=dell actually, but in your case it would be model=hp). I still don't get any sound from any of the mixers, but at least I have some options to choose from.

Also, here's my alsa-info.sh output, if it's any help: [http://www.alsa-project.org/db/?f=8a166ff9aa4c1544893e96c04bd8147f434a4095](http://www.alsa-project.org/db/?f=8a166ff9aa4c1544893e96c04bd8147f434a4095)

---

### Post by gmorphis on 2009-04-28
I have sound!!!!!!
So this is what I did.. 
edited alsa-base.conf
sudo gedit /etc/modprobe.d/alsa-base.conf

at the bottom, add these lines
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=hp 
options snd-hda-intel enable_msi=1

The first 2 should be there already. Afterwards I still didnt have sounds.. I restarted and one heard one conga beat.. I thought this was the answer.. alas no sound.. then I started playing around checking settings.. I still had "NULL OUTPUT" for Output Devices in PulseAudio Volume Control. I clicked the Configuration Tab. I only had "Input Analog Stereo" selected. I chose the top option Output Analog Stereo + Input Analog Stereo and bam I had sound! I don't know why only the Input Analog was selected, I didnt do it.
So if you're in my boat, add those lines to your alsa-base file and check the Volume Control Configuration setting.. Now I can begin to learn Linux, thanks guys!

---

### Post by mistamorse on 2009-06-11
Thank you gmorphis!

I was having the same problem on:

Gateway M275 tablet
SB Audigy 2 NX USB sound card

I edited  /etc/modprobe.d/alsa-base.conf, restarted, and that darned 'Null output' was gone!

---

