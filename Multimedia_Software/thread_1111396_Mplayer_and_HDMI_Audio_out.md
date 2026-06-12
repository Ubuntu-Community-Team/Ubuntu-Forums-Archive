---
title: "Mplayer and HDMI Audio out"
date: 2009-03-30
forum: Multimedia Software
---

### Post by psunix on 2009-03-30
Hi

I got a problem with mplayer and audio over hdmi.

Ubuntu 8.10 - the Intrepid Ibex

Audio out works when I use the default "Movie Player" but when I use mplayer to play any movie, it doesn't work.
The default device for audio output under System > Preferences > Sound is "HDA NVidia NVIDIA HDMI (ALSA). This device was available after I upgraded Alsa to its newest version.
Can somebody tell me how I can figure out which device ubuntu is using for playback? I don't know what device I need to tell mplayer. "mplayer -ao alsa:device=??????"
Where are these sound settings saved in ubuntu? 
Does ubuntu use pulseaudio?

Thanks for your help

Psunix

---

### Post by psunix on 2009-04-11
Hi 

I figured out how to access the right audio device over ALSA.

 mplayer -ao alsa:device=hw=0.3

It works, but there is a strange problem. When I start a movie or audio file, mplayer hangs for about 10 sec until it starts playing.

Does anyone know why this may happen?

---

### Post by zosky on 2009-06-01
> **psunix said:**
> 
It works, but there is a strange problem. When I start a movie or audio file, mplayer hangs for about 10 sec until it starts playing.

Does anyone know why this may happen?

i built [_XBMCbuntu_]("http://www.xbmc.org/wiki/?title=XBMCbuntu") w/ Jaunty minmal CD
[_forcing Alsa to hdmi_]("http://ubuntuforums.org/showpost.php?p=6690552&postcount=4") (hw:1.3) using /ect/asound.conf

i can report the same thing... 
~2sec no audio after starting, FF'ing, RWd'ing...

is this a bug in ubuntu 
or alsa or something i can configure ?
(this does not happen on analog)

---

### Post by bcg30506 on 2013-01-06
> **psunix said:**
> Hi 

I figured out how to access the right audio device over ALSA.

 mplayer -ao alsa:device=hw=0.3

It works, but there is a strange problem. When I start a movie or audio file, mplayer hangs for about 10 sec until it starts playing.

Does anyone know why this may happen?

Mine is still silent even with the above command (except mine is 1.7).  It works great in mythfrontend.  I get no error messages, just no sound.  Same with VLC.  No audio.  The device in mythtv that works well is ALSA:hw:1,7.

---

