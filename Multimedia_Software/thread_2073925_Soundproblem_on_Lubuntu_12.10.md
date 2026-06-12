---
title: "Soundproblem on Lubuntu 12.10"
date: 2012-10-20
forum: Multimedia Software
---

### Post by Svante65 on 2012-10-20
Having some sound problems with my Samsung N120 Netbook.
I'm using the new Lubuntu 12.10.
If I e.g. play a youtube video the sound is on, but if I try to play another one, there is no sound at all. Same problem with other "sound sources" like mp3.
The only thing I can do, is to boot the machine :(

---

### Post by echolink on 2012-10-20
Lubuntu uses Alsa by default as its sound server. Recently on 12.04, and 12.10 I have installed pulseaudio as a replacement. Pulse audio has several advantages of over Alsa, one of them being multichannel audio. Just use:

```
sudo apt-get install pulseaudio pavucontrol
```

Now I just need to find out how to submit it on Launchpad as a proposal for Lubuntu 13.04 lol

---

### Post by Svante65 on 2012-10-21
> **echolink said:**
> Lubuntu uses Alsa by default as its sound server. Recently on 12.04, and 12.10 I have installed pulseaudio as a replacement. Pulse audio has several advantages of over Alsa, one of them being multichannel audio. Just use:

```
sudo apt-get install pulseaudio pavucontrol
```Now I just need to find out how to submit it on Launchpad as a proposal for Lubuntu 13.04 lol
Tried to install Pulseaudio. That didn't help :(

---

### Post by Svante65 on 2012-10-22
Looks like, it's not a Lubuntu problem. I have the same issue with Ubuntu and Kubuntu.

May be it's a kernel problem?

---

### Post by Svante65 on 2012-10-31
Anyone beside me having these issues?

---

### Post by Ionic-user on 2012-10-31
Having to reboot after one single play, no, Lubuntu plays audio, streamed and recorded files well on my netbook (AOA 110, 1st gen.) but I'm still trying to get Audacity to record streamed audio without benefit of Pulse to aid Alsa. Haven't found a way of doing this yet (RTFM? - did that) whereas on Ubuntu and SolusOS, it is possible as pavucontrol and Alsa cohabit well apparently. Also don't want to screw up a sound system that works, even with bloody Skype!

---

### Post by ajregester on 2013-01-31
+1, Same problem here with Lubuntu 12.10 and an Acer Aspire One 725.

---

