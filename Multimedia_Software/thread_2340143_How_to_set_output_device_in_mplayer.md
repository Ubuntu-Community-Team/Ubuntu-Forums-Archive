---
title: "How to set output device in mplayer"
date: 2016-10-16
forum: Multimedia Software
---

### Post by bill-lancaster on 2016-10-16
I have a bluetooth speaker connected to my pc.
Amarok plays to it OK.
How can I get mplayer to play to it.
In terminal:-
~$ mplayer -ao help
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Available audio output drivers:
        pulse   PulseAudio audio output
        alsa    ALSA-0.9.x-1.x audio output
        oss     OSS/ioctl audio output
        jack    JACK audio output
        sdl     SDLlib audio output
        v4l2    V4L2 MPEG Audio Decoder output
        null    Null audio output
        pcm     RAW PCM/WAVE file writer audio output

I have tried ~$ mplayer -vo xxxxx for each of the output drivers (except the last two) but with no result.
When executing ~$ mplayer -vo xxxxx I just get the mplayer version and options list, does this indicate that the instruction wasn't accepted?

Any advice would be appreciated

Kubuntu 14.04

---

### Post by SeijiSensei on 2016-10-16
Those are alternative audio output drivers and require the "-ao" switch just like you used to list them with "-ao help".

Did you configure pulseaudio to use the Bluetooth speaker by default?

---

### Post by bill-lancaster on 2016-10-17
Thanks for the response.
How do I configure pulseaudio please?
Amaraok has something called 'phonon' which has bluetooth speaker as default.

---

### Post by SeijiSensei on 2016-10-17
I think that should work without any changes.  Try using "mplayer -ao pulse /path/to/some/media" and see if that works.

---

### Post by bill-lancaster on 2016-10-18
No luck!

---

### Post by bill-lancaster on 2016-10-18
OK, success!
Looked at Pulseaudio Volume Control and turned of buit-in-audio leaving bluetooth sound link on.
Don't know what I'm doing but it works!
Thanks again

---

### Post by SeijiSensei on 2016-10-18
In Kubuntu, I remove the default kmix volume control application from the panel and the system.  In its stead I run
```

sudo apt-get remove kmix
sudo apt-get install plasma-widget-veromix
```

Once you've run those commands, you can click on the "cashew" at the right end of the panel, choose Add Widgets, then add the widget for Veromix.  You'll be able to switch between input sources and output devices on-the-fly.  Highly recommended.

---

