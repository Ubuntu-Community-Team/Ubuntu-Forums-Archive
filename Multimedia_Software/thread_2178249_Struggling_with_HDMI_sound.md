---
title: "Struggling with HDMI sound"
date: 2013-10-02
forum: Multimedia Software
---

### Post by chris134 on 2013-10-02
Hi

I'm trying to get sound working in a Mythbuntu installation.I have managed to get sound working in Mythtv by selecting the entry in the Frontend setup of 

ALSA:plughw:CARD=NVidia,Dev=9

This plays sound through my TV speaker no problem.  I cant get any sound though out of other application like VLC or Spotify.

I have the following in /etc/asound.conf

pcm.!default {
        type plughw
        card 0
        device 9
}

Which isfrom a link i found on the net somewhere but i cant get any sound to play from the speakers.

The following works from the CLI and sound is heard

aplay -D plughw:0,9 /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

but this doesnt, it says its playing but no sound is made.

aplay -D default /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono

ANy advice greatfully received!

Chris

---

### Post by Yellow Pasque on 2013-10-02
Maybe try:
```

pcm.!default {
  type plug
  slave {
    pcm "hw:0,9"
  }
}
```

---

### Post by chris134 on 2013-10-03
Well this is strange

I have since discovered that VLC is actually making sound.  the results of the aplay commandsabove are inchanged.

Spotify still makes no sound.  I have tried changing asound.conf as suggested above,its made no difference.

Any other suggestions?

CHris

---

