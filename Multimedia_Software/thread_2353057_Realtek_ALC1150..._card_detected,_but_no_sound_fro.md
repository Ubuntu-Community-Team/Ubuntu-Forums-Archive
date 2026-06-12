---
title: "Realtek ALC1150... card detected, but no sound from output jacks"
date: 2017-02-18
forum: Multimedia Software
---

### Post by neurodancer on 2017-02-18
I have Ubuntu 16.10 running on an Asus Sabertooth Z97 Mark 2 motherboard. This motherboard has a Realtek ALC1150 sound chip.

It is supposed to be supported by ALSA as an Intel HDA sound card, and ALSA does detect it, and it can be manipulated by utilities, and I can even use Clementine or other sound software to play through the device. VU meters even show output.

However, there is no sound, and the sound card shows unplugged on all ports in ALSA and Pulse utilities.

I have an nVidia GTX 690 GPU, and audio through it and the GK104 driver works. I would just punt and use this but my display monitor's sound port is damaged.

I bought a super cheap USB sound dongle so I at least have some sound until I figure out what is wrong with the on-board sound.

Debugging Information:

Running aplay -L I see that the ALC1150 shows up as Card=PCH, while the nVidia audio shows up as Card=NVidia.

The Intel/Realtek and the nVidia sound hardware seem to controlled by the ALSA module snd_hda_intel so I wondered if maybe that causes a conflict of some kind.

Normally when a driver cannot be found, you get an error trying to play audio, but in my case ALSA sees the card, Pulseaudio sees it... mp3 players can play to it, but there is no sound and the port status shows unplugged.

Another item: The Unity sound preferences only shows a digital stereo output for the ALC1150, at odds with Pulse and ALSA utilities.

I ran also-info and the rest of this post is that information.

Hopefully someone can help me out with this. I feel like ALSA supports my motherboard sound just fine, and there is some minor error somewhere.

Output of alsa-info can be found at the alsa-info website: [http://www.alsa-project.org/db/?f=a3560967f5682f6b2418465223b8f7fd41dcc2d4](http://www.alsa-project.org/db/?f=a3560967f5682f6b2418465223b8f7fd41dcc2d4)

---

### Post by cariboo on 2017-02-20
Check to see if the everything is turned up in alsamixer.

[[img]https://s11.postimg.org/rkfhzsigf/Screenshot_2017_02_20_15_38_04.png[/img]](https://postimg.org/image/rkfhzsigf/)

---

