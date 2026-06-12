---
title: "No sound. Always boots to mute"
date: 2009-05-17
forum: Multimedia Software
---

### Post by andrewabc on 2009-05-17
I am running 64bit ubuntu 9.04, on ext4.
I have realtek sound card (HDA Intel).
It is possible to have sound for short amount of time, but it rarely works.

I start computer, and master volume is muted and turned down all the way. It is like this every time I restart, even if I change the settings.

When the computer starts and desktop loads, if I am very quick, I unmute master volume, turn up master volume to say 50%, sometimes PCM is turned down all the way (or muted, it is random) so I have to turn it back up all the way. I start music player and music plays (and I hear it). But if I pause music for more than 5 seconds or so, the sound stops and does not start again when I unpause music. I've tried different sound settings (alsa, pulseaudio etc) in system->preferences sound

So for whatever reason, sound is possible, but rarely works.
Master volume is muted on boot 99.9% of time.
PCM is muted or turned down all the way on startup.

I have tried alsa mixer, but that does same thing as gnome one.

Why does it always start muted?
Sound worked fine from 6.06 to 8.10
I've read most threads and tried lots of stuff but nothing works.

I enabled proposed updates, and there was a sound update but it did nothing. Even the new kernel did not prevent the system shutdown beep (which it was supposed to fix).

aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lspci -v
> 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Foxconn International, Inc. Device 0cef
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at efff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by andrewabc on 2009-05-18
After a couple hours of testing, it seems that music program Sonata and MPD were messing with sound. If playing, then left on pause and then computer restarted, there sound would always start muted and never work. If I stopped sonata music before shutdown it works normally on reboot.
I also switched everything in system->preferences->sounds to pulseaudio, but I think it now works with autodetect as well.

So for now I guess I will switch to audacious and hope to have no more problems.

EDIT:
I left audacious open and paused and restarted and there is no sound on reboot. So it seems you cannot have any program using sound running while shuting down computer?
EDIT:
Turns out it was sonata+mpd again messing it up.

---

### Post by NTolerance on 2009-09-03
I'm also having this problem.  I'm using ampache and mpd.  When I stop mpd playback and clear the playlist, the master volume is muted.

---

### Post by andrewabc on 2009-09-05
> **NTolerance said:**
> I'm also having this problem.  I'm using ampache and mpd.  When I stop mpd playback and clear the playlist, the master volume is muted.

Hi. I stopped using MPD and the problem went away.

I think it could have because I had MPD using custom alsa preferences which was messing things up. These custom settings had worked fine in Intrepid 8.10.

I'd recommend stop using MPD for now if you want sound. I am using audacious. Hopefully it will be fixed in 9.10. Maybe try a liveusb or something to see if it works on it.

---

### Post by NTolerance on 2009-09-05
> **andrewabc said:**
> Hi. I stopped using MPD and the problem went away.

I think it could have because I had MPD using custom alsa preferences which was messing things up. These custom settings had worked fine in Intrepid 8.10.

I'd recommend stop using MPD for now if you want sound. I am using audacious. Hopefully it will be fixed in 9.10. Maybe try a liveusb or something to see if it works on it.

I actually just fixed this problem.  Edit /etc/mpd.conf and change 

```
mixer_type                      "alsa"
```
to
```
mixer_type                      "software"
```

---

### Post by nortexoid on 2009-09-23
I have *part* of your problem. Whenever I set the volume unmuted and restart, it goes back to being muted at the beginning. I have no other problems with sound however, so it's not that big a deal, but still, what's the deal?

---

### Post by parul1234 on 2009-09-23
Thanks for the help . I also had the same problem with my ubuntu installation on my laptop.

---

### Post by Wlerin on 2009-09-23
> **nortexoid said:**
> I have *part* of your problem. Whenever I set the volume unmuted and restart, it goes back to being muted at the beginning. I have no other problems with sound however, so it's not that big a deal, but still, what's the deal?

I have this problem as well. It's not too serious, but it shouldn't be happening either.

---

### Post by sideaway on 2009-09-24
I have this issue as well, however, I do not have MPD installed?

---

### Post by Wlerin on 2009-09-24
[http://ubuntuforums.org/showpost.php?p=1213829&postcount=4](http://ubuntuforums.org/showpost.php?p=1213829&postcount=4)

This is also mentioned in the third sticky.

---

### Post by sideaway on 2009-09-27
> **Wlerin said:**
> [http://ubuntuforums.org/showpost.php?p=1213829&postcount=4](http://ubuntuforums.org/showpost.php?p=1213829&postcount=4)

This is also mentioned in the third sticky.
hamish@hamish-desktop:~$ sudo alsactl store 0
E: core-util.c: Home directory /home/hamish not ours.
hamish@hamish-desktop:~$

---

### Post by Wlerin on 2009-10-07
Try it without sudo. Although... it doesn't seem to have worked for my machine either.

---

### Post by whittaker007 on 2009-12-02
I have this same problem, seems to be unrelated to software conflicts - I can restart, set the volume to any level, start no other software (except whatever is set to autorun) and restart. It's muted again.

I've tried running **alsactl store** and **alsactl store 0** as the current user, as well as root. It seems that running the **alsactl restore** command does work, but only if the volume is nonzero when you execute it. Of course it always starts at zero and restore does not work.

I've deleted /var/lib/alsa/asound.state and tried **alsa force-reload** (which warns that it can't stat various daemons and that pulseaudio is using the device). Nothing has helped.I also can't get AC3 passthrough working on VLC or MoviePlayer - only XBMC.

---

### Post by Zopiac on 2009-12-18
I too have had this problem for a month or so, same volume problems, only started when I upgraded to 9.04.
I do not have mpd installed, nor does alsactl work, sudo or not.
Lastly I have no clue how to fix it :\

---

### Post by kybernetes on 2009-12-19
I have the same issues with 9.10 - Karmic Koala, pulseaudio 0.9.19. 

It already took me 2 days to get sound at all, so i'm glad that it's just about storing the mixer levels between reboots.

---

### Post by whittaker007 on 2009-12-20
Yeah, it's not quite that simple unfortunately. I've managed to get sound (both stereo and AC3 passthrough) working on either VLC or XBMC and occasionally both (but not always). Also my volume levels are getting restored on reboot, but sometimes muted. I have never been able to get digital sound out working on MythTV despite having apparently the same settings as XBMC.

And after a recent update any video I play through MythTV inverts the colours in the video and goes on to invert colours in XBMC and VLC which persists until a reboot. And I can't get a headless VNC session to work at all no matter what config settings I use. :confused:

I'm considering downgrading my system to Jaunty. Does anyone know if digital sound and hardware accelerated video work properly on Jaunty? Or do I have to go back further than that?

---

