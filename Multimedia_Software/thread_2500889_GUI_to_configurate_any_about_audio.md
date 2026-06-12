---
title: "GUI to configurate any about audio"
date: 2024-09-15
forum: Multimedia Software
---

### Post by Juan_Jess_Parede on 2024-09-15
I'm using Ubuntu Studio 24.04.1 LTS, with PulseAudio, Jack and PipeWire.

I know about qjackctl and qpwgraph and its capabilities to connect and disconnect audio devices in and out of computers.

BUT... Non of them give us the "power" to FULL configurate Alsa, PipeWire, Jack and/or PulseAudio.

I'm talking about to setup things like: number of input/output channels, name of the channels, buffer(s) size, number of samples and bits, etc.

We have to do these operations editing the configuration files of each server.

BUT... To do that editing process... We have to know about the extraterrestrial language of the computing programmers!!!

We, the users, don' t want or need to learn about that. That's the reason GUI apps exist!!!

So... I need to know... Is there some GUI app to FULL configurate ALL about the sound in our computers? ???

BTW... I'm not an enemy of programmers. I just want something so easy like old audio amplifiers!!! Those amps have very simple controls on the front face and very easy input and output connectors on the back face. Why not the same on the screen? ???

---

### Post by bobunderwood99 on 2024-09-15
The short answer to question 1 is no.

Use [https://ubuntustudio.org/audio-configuration/](https://ubuntustudio.org/audio-configuration/) to set global sample rate and quantum (buffer size).

Use PulseAudio Volume Control to select appropriate ALSA sound card profile.

Stick with qpwgraph (not qjackctl).

You could look at [https://github.com/dimtpap/coppwr](https://github.com/dimtpap/coppwr)

---

### Post by Juan_Jess_Parede on 2024-09-20
Thank you so much for your answer!!!
I've tried any kind of different editing inside the pipewire configuration files (etc/pipewire, usr/share/pipewire, usr/share/pipewire.conf.d and /home/.config/pipewire) and... Nothing!!!
It seems like pipewire, in my computers, just recognizes stereo sound (Left and Right) channels.
But, all my computers have 7.1 surround sound systems!!!
Before the upgrading from 22.04.4 to 24.04.1 I got all the 7.1 surround audio channels from MPVPlayer, VLCPlayer, SMPPlayer, DragonPlayer, and even Adobe Audition through WineHQ!!!
Today, I just get stereo audio, I don't know why.
That's what it is.

---

### Post by bobunderwood99 on 2024-09-20
If you want 7.1 surround choose the appropriate profile in PulseAudio Volume Control. What profiles do you see?

---

