---
title: "ALSA stopped working..."
date: 2008-09-18
forum: Multimedia Software
---

### Post by Zorgoth on 2008-09-18
Ubuntu 8.04 64-bit:

I recently got a Logitech USB headset and made it default by editing /etc/modprobe.d/alsa-base as prescribed by the sticky, and the headset later broke.  I have a new headset, and now ALSA doesn't work with it or my regular sound card, although I reverted the changes to /etc/modprobe.d/alsa-base; I am using PulseAudio now for normal speakers and the USB Audio option for my headset, and ever since I started that many programs have lost their sound, mostly games.  I have certainly rebooted my computer many, many times.  I tried reinstalling alsa-base and alsa-utils but that had no effect.

My regular sound card is some kind of SigmaTel thing I think and my new headset is a Plantronics USB headset.

When I try to make a test sound I get the following errors:

Sound Events: 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Music and Movies:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Audio Conferencing Playback: 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

Audio Conferencing Capture: 
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.


I still get sound from system sounds and sounds made by programs that came with the OS (except Totem, which lost sound), Flash Player, Skype ,and Audacity (the last two can detect the devices directly I think).

Thanks in advance!

---

### Post by markbuntu on 2008-09-19
You can try my troubleshooting thread here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

