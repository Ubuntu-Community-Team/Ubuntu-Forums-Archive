---
title: "vlc and hdmi audio"
date: 2009-03-12
forum: Multimedia Software
---

### Post by brombo on 2009-03-12
I am running ubuntu 8.10 amd64 on an ASUS M3N78 PRO motherboard. The motherboard has NVidia video and audio (HDA/HDMI).  The video works fine with vlc and mplayer (playing a dvd), but I get no audio.  Video and audio work with totem.  I can record and play audio with audacity with the following settings:

Output -
ALSA:HDA NVidia:NVIDIA HDMI (hw:0,3) using Portaudio v19

Input -

ALSA:HDA NVidia:ALC 1200 Analog (hw:0,0)

When I say play audio I mean the hdmi output of the motherboard to my television.

Could anyone give me direction as to how to set up vlc and/or mplayer for at least getting audio for dvd playback and hopefully for recording audio (video I can do) with vlc and/or mplayer.

Thank you very much in advance.

---

### Post by sunscan on 2009-04-18
Same problem and same motherboard. Did you find a solution? :(

---

### Post by Axess_Denied on 2009-09-18
Similar issues using an Asus board with ATI HDMI out. Exaile, Banshee all play through the HDMI out, but I get no audio from VLC or MPlayer.

*bump*

---

### Post by beastrace91 on 2009-09-18
Hey There - audio via HDMI is a pain in the @$$ on most Linux apps to say the least. Give [this thread](http://www.linuxquestions.org/questions/linux-hardware-18/audio-through-hdmi-cable-733378/) a once over. In the end I ended up buying an 1/8 inch to RCA cable just because the time spent tinkering with it was no longer worth it.

Best of luck,
~Jeff

---

### Post by brainkilla on 2009-09-19
> **brombo said:**
> I am running ubuntu 8.10 amd64 on an ASUS M3N78 PRO motherboard. The motherboard has NVidia video and audio (HDA/HDMI).  The video works fine with vlc and mplayer (playing a dvd), but I get no audio.  Video and audio work with totem.  I can record and play audio with audacity with the following settings:

Output -
ALSA:HDA NVidia:NVIDIA HDMI (hw:0,3) using Portaudio v19

Input -

ALSA:HDA NVidia:ALC 1200 Analog (hw:0,0)

When I say play audio I mean the hdmi output of the motherboard to my television.

Could anyone give me direction as to how to set up vlc and/or mplayer for at least getting audio for dvd playback and hopefully for recording audio (video I can do) with vlc and/or mplayer.

Thank you very much in advance.

For mplayer try this 
```
mplayer -ao alsa:device=hw=0.3
```

It worked in my setup, with ASUS M3N78-ME mobo. Put a .asoundrc file in your home dir with following contents

```
pcm.!default { 
type hw 
card 0 
device 3
} 

```

and you will have everything set up for mplayer usage. My problem lies in the fact I cannot manage to get audio working in Totem and Boxee...

---

