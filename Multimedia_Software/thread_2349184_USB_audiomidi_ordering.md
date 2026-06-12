---
title: "USB audio/midi ordering"
date: 2017-01-11
forum: Multimedia Software
---

### Post by vostoklake on 2017-01-11
Okay, I've been experimenting with creating a fixed order for my various USB audio and MIDI cards, as explained here: [https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices) - so that each card I use will have a fixed ALSA device number (hw:X).

I've come into a problem which took up a lot of my time until I gave up and went for a work-around. Basically I got a cheap and cheerful CH345-chipset MIDI controller and it took ages trying to assign an index number to it. It would always conflict with either the onboard HDA Intel sound card, or the USB sound card.

Eventually I realised that it was insisting on taking either slot 0 or slot 1 at all times. So I just shrugged, gave it that number and ordered the other cards around it - which seems to be working.

I know CH345 is problematic to say the least but I'm not sure why it would be playing up with ALSA like this. Any ideas?

---

### Post by wildmanne39 on 2017-01-12
*Thread moved to **Multimedia Software**.*

---

