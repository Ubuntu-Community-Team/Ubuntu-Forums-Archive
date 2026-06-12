---
title: "Sound mysteriously stopped working (in some cases!) in 8.10"
date: 2009-03-06
forum: Multimedia Software
---

### Post by adambr on 2009-03-06
I've been using 64-bit 8.10 for awhile now, and have had no sound problems until today.

The initial situation:  As of yesterday, all sound was working fine.  Sounds in games (like Nexuiz) or in flash (like firefox/opera+youtube or wine+firefox+youtube) or just plain audio/video applications (like vlc or Rhythmbox) worked great, even for multiple applications running at the same time.

What has changed:  No hardware anything is different.  I believe I installed the latest updates for my system last night before I went to bed (so it might be this) and shut down my computer.  Also, this morning my wife tried to play an audio CD in our computers CD player (something that we have oddly never tried before under ubuntu).  I was asleep at the time, but she claims she was only able to play one of the audio tracks...I'm not sure if this is at all related.

The new situation: Ok, this is where it gets strange (in my noobish opinion).  First, when I try to play audio through any of my normal routs (such as Rythmbox or firefox+youtube etc), a very low crackling comes through my speakers.  However, in my search for a solution to this problem, I have come across several situations where audio does work.  Things I have tried so far:

1) In a forum which I lost track of, I was reading about ways to check if your audio was working.  One suggestion was:

sudo cat /dev/urandom > /dev/dsp

...which seems to be working as expected.  That is, a tv-esk static sound (different from and more regular than the crackling coming through when playing an MP3) comes through my speakers when this is exectued.  

2) sudo alsamixer

This works and the Master volume level is set at 100 <> 100.

3) gnome-sound-properites

When I run this application, I am given many options for the various sound output devices at my disposal for things like Sound Events and Music and Movies (etc).  Here are a list of the output devices for Sound Events:

Autodetect
HDA NVidia STAC92xx Digital (ALSA)
HDA NVidia STAC92xx Analog (ALSA)
HDA NVidia STAC92xx Digital (OSS)
HDA NVidia STAC92xx Digital (OSS)
HDA NVidia STAC92xx Digital (OSS)
ALSA - Advanced Linux Sound Architecture
OSS - Open Sound System
PulseAudio Sound Server

Here is what happens when I press test when each of the above is selected:
------------------------------------------------------------------------
Autodetect
Crackling sound from the speakers

HDA NVidia STAC92xx Digital (ALSA)
No sound

HDA NVidia STAC92xx Analog (ALSA)
An error popup appears saying:
"audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback"

HDA NVidia STAC92xx Digital (OSS) (first one)
A sound is played from my speakers (what sounds like a sine wave)

HDA NVidia STAC92xx Digital (OSS) (second one)
A sound is played from my speakers (what sounds like a sine wave)

HDA NVidia STAC92xx Digital (OSS) (third one)
No sound

ALSA - Advanced Linux Sound Architecture
Crackling sound from the speakers

OSS - Open Sound System
A sound is played from my speakers (what sounds like a sine wave)

PulseAudio Sound Server
Crackling sound from the speakers
------------------------------------------------------------------------

Now, I have tried setting all of the drop-down's in this application to OSS as that is obviously working, but audio still fails to play (IE crackling from my speakers) when using any normal application (firefox, games, Rythmbox, etc).

---

### Post by crunchfighter on 2009-03-06
Try this thread:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=streaming+tv](http://ubuntuforums.org/showthread.php?t=789578&highlight=streaming+tv)

---

### Post by adambr on 2009-03-08
Thanks a bunch!  That worked!

(IE Part C from the link)

---

### Post by scohar70 on 2009-04-20
I just wanted to chime in as well.  I'm also running Intrepid 8.10 64 bit mode, and had the EXACT same problems as described by adambr.  The fix suggested by crunchfighter totally worked for me.

I have no idea why ALSA would stop working all of a sudden, but running the [FONT="Courier New"]alsamixer -Dhw[/FONT] command fixed it.

---

