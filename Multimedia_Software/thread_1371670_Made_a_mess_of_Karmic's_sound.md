---
title: "Made a mess of Karmic's sound"
date: 2010-01-03
forum: Multimedia Software
---

### Post by Omicron Machine on 2010-01-03
So, to start at the beginning, I had upgraded a Jaunty install to a Karmic one on my HP laptop with all Intel hardware. Everything worked just fine, sound, peripherals, Compiz, all that. Then I messed it up doing unrelated fiddling around, and had to do a clean install. After that, I had sound problems (and Compiz problems, but first things first, and that would need its own thread elsewhere anyways).

First, I had no sound to the headphones at all, and there was no option under sound preferences to turn on the headphone jack detection, so I set a script to do it manually each time I log in, using Preferences> Startup applications. This is it:
> #!/bin/bash

amixer -c 0 sset 'Headphone Jack Sense' unmute

This worked in that it turned on the headphones, but plugging in the headphones didn't (and still doesn't) turn off the speakers, giving sound in both places at once. While trying to fix this, I tried reinstalling ALSA packages from Synaptic, and when that didn't work, tried this: [http://ubuntuforums.org/showthread.php?t=1046137]("http://ubuntuforums.org/showthread.php?t=1046137"), but it didn't seem to have any effect. I tried switching from ALSA to OSS, but I lost a bunch of functionality, and that only made it worse so I switched back to ALSA. But a bunch of stuff still doesn't work.

At the moment, I have sound from Firefox and from system sounds, but none from any movie or music player (I even downloaded a bunch and tried different ones). I have another thing that runs on login, using aplay to play a .wav file. That one plays right when I login, and I can make it play again from terminal, but another .wav file that used to play correctly from terminal no longer does:

> aplay: set_params:979: Sample format non available


The sound preferences, and aplay -l detect no soundcards, but lspci does, and /proc/asound/ doesn't exist. That error combined with those facts implies it might be a headers or modules thing, but sudo apt-get install linux-generic says everything is up to date. I also have no sound at the login screen, which used to work fine, and which I'd really like back because I have a custom sound I put there myself that I was rather proud of.

I've also done a lot of updating and reinstalling and trying alternatives to, and switching back to, things like pulseaudio and other related things, and I've done my damnedest to get things back the way they were, and I think they're pretty close except for the above-mentioned differences, but I'm not even sure where things are at right now.

Any clue what I did wrong, what to do about it, and how not to do it again in the future?

---

### Post by Omicron Machine on 2010-01-03
Actually, Exaile, another music player, is playing everything properly. Still nothing out of Rhythmbox, no login screen sound, and no sound on video. So Exaile's decided to work, but everything else is the same as before.

---

### Post by Yellow Pasque on 2010-01-03
Exaile and Rbox both use gstreamer, so it's odd that one plays and one doesn't (assuming you have all the appropriate gstreamer packages/codecs).

Also, it's not clear whether you're running pulseaudio.

---

### Post by Omicron Machine on 2010-01-03
I just checked my installed gstreamer stuff in Synaptic, and everything looks fine. Pulseaudio is installed, the volume applet works, but it doesn't detect my hardware anymore either. I'm not sure if that constitutes running. I'm a little confused what I've still got setup how myself at this point. I've been adding and removing things with various results all day, but I've described the major changes at least to the best of my memory and ability. Even just getting the original problem with the headphones back would be nice.

---

### Post by Omicron Machine on 2010-01-07
Turned my computer off, turned it back on in the morning. Exaile no longer has sound. I can only get sound through Firefox now. The aplay command at login still plays, not sure about system sounds, but not noticed any today I don't think.

---

### Post by Yellow Pasque on 2010-01-07
Starting exaile from a command line might be helpful..
For system sounds, try:
```
canberra-gtk-play --file=<path to file>
```

---

### Post by Omicron Machine on 2010-01-07
On typing in just "exaile":
>  File "/usr/lib/exaile/exaile.py", line 56, in <module>
    main()
  File "/usr/lib/exaile/exaile.py", line 53, in main
    exaile = main.Exaile()
  File "/usr/lib/exaile/xl/main.py", line 77, in __init__
    self.setup_logging()
  File "/usr/lib/exaile/xl/main.py", line 266, in setup_logging
    mode='a', backupCount=5)
  File "/usr/lib/python2.6/logging/handlers.py", line 107, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/handlers.py", line 59, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/__init__.py", line 819, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 838, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '/home/technomancer/.config/exaile/exaile.log'


On using "sudo exaile" for some reason (it used to work normally, now it won't open from the applications menu, just like this), it opens normally but without sound.

For the other bit, no matter what I try to play, system sound or otherwise, regardless of location or format, I get: "Failed to play sound (callback): Access forbidden".

---

### Post by Yellow Pasque on 2010-01-07
Look in the sound guides for suggestions on adding your user to the proper groups for audio.

pulse
pulse-access
pulse-rt

---

### Post by Omicron Machine on 2010-01-07
I am in the sound group, I just checked. Logged out, logged back in, still everything the same. I'm not sure what the other three things were, but I tried putting them into the terminal, and they were all "Command not found."

---

### Post by Yellow Pasque on 2010-01-07
Those are the groups your user needs to be in.

---

### Post by Omicron Machine on 2010-01-07
Thanks. I added myself to the first two, but it said the last one didn't exist. Should I make it and add myself, or would that not be the same thing?

---

### Post by Omicron Machine on 2010-01-07
Also, I just noticed Audacity has sound, but I didn't check that particular application before, and since nothing else has changed, I assume it worked from the start. I also did the "Getting the ALSA drivers from a *fresh* kernel" bit from the Comprehensive Sound Guide ([http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")) because it said it was a good way to reverse problems incurred by tinkering, but the purge and reinstall they recommended there didn't change anything either. I remembered to reboot and/or logout after each thing I've been trying.

EDIT: Just re-tried Amarok, even though I have gnome, but it had worked previously (except for crapping its pants and making Linda Blaire noises when it went to play a .wav, but that's neither here nor there) at the same time that Exaile was. It not longer has sound either. Still have the successful login noise, but no login screen noise.

---

### Post by Omicron Machine on 2010-01-07
Now I'm not even getting sound out of Firefox as of this morning. What the crap.

---

### Post by VertexPusher on 2010-01-07
Do a clean install, then remove PulseAudio. This is how to do it properly:

Install gstreamer0.10-alsa and gnome-alsamixer. Then remove gstreamer0.10-pulseaudio, vlc-plugin-pulse and pulseaudio. Then reboot.

I wonder why so many people try to fix PulseAudio by removing ALSA and installing OSS. Pulse and ALSA are totally separate things. OSS will fix exactly zero PulseAudio bugs but most likely add some issues of its own.

Stick to the stuff that works.

---

### Post by Omicron Machine on 2010-01-07
A whole clean install? Did I really mess it up that badly?

---

### Post by VertexPusher on 2010-01-07
> **Omicron Machine said:**
> A whole clean install? Did I really mess it up that badly?
That's hard to figure out from here.

You asked for a fix three days ago. How long would a clean install take on your computer? 30 minutes?

---

### Post by Yellow Pasque on 2010-01-07
I'd recommend trying the ALSA upgrade script before surrendering to a full reinstall. [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by Omicron Machine on 2010-01-07
It's not the installing, it's the complete and full backing up. With my setup here, that's the long, boring and tedious part.

---

### Post by Yellow Pasque on 2010-01-07
You should put root and home/personal data on different partitions if possible (makes life easier).

---

