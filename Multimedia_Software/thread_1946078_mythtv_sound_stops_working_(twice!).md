---
title: "mythtv sound stops working (twice!)"
date: 2012-03-24
forum: Multimedia Software
---

### Post by superfrank on 2012-03-24
So I have had mythtv working for a while, then all of a sudden 2 weeks ago the sound stopped working in mythtv. I was able to play sounds with a command line utility, but there was no sound from mythtv. I had mythtv set to play from the default sound device and hadn't changed anything there.

After trying lots of things I eventually reinstalled ubuntu (yes I know, desperate times!) and sound was working again. However after a couple of days it stopped!

One thing I noticed is that when the sound was working, there were the following ALSA entries in myth's frontend log:
> 2012-03-23 21:13:39.785 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 32 bit reenc 0
2012-03-23 21:13:39.786 ALSA, Error: Setting hardware audio buffer size to 6016
2012-03-23 21:13:39.786 ALSA, Error: Error opening /proc/asound/card0/pcm0p/sub0/prealloc: Permission denied. 
2012-03-23 21:13:39.786 ALSA, Error: Try to manually increase audio buffer with: echo 6016 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
2012-03-23 21:13:39.786 ALSA, Error: Unable to sufficiently increase ALSA hardware buffer size - underruns are likely
2012-03-23 21:13:39.788 AudioPlayer: Enabling Audio

While now that sound stopped working it changed to an error about not finding the mixer:
> 2012-03-23 22:14:39.716 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2012-03-23 22:14:39.718 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2012-03-23 22:14:39.761 ALSA, Error: no playback control PCM found on mixer device default
2012-03-23 22:14:39.761 ALSA, Error: Unable to open audio mixer. Volume control disabled
2012-03-23 22:14:39.761 AudioPlayer: Enabling Audio
So it seems to me that the default ALSA sound device as detected by mythtv has changed. Why would this happen?

---

### Post by BicyclerBoy on 2012-03-24
Where do you get your mythtv fix from?

The audio code has had a lot of work during 0.24+fixes, some of these changes were to do with audio buffer sizing.

Have you re-scanned audio devices in myth frontend setup?
Do you have any other options ticked: resample, upmix, AC3 etc
How is the PC audio connected to TV/AVR?

---

### Post by superfrank on 2012-03-26
I'm getting the latest mythtv packages from the mythbuntu updates every few days.

Rescanning audio devices doesn't make any difference. I've started off with no options ticket but then tried some options while attempting to fix it. As far as I know, I've not touched the audio settings and they've worked for a while then randomly stopped one time when I restarted mythtv.

The connection is via S-Video + Audio. I was able to play sound via aplay which suggests that the problem lies within mythtv.

I saw in another post these two links so I'll work through them when I get home tonight:

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit?pli=1)
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

