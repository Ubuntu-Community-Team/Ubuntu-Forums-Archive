---
title: "Sound gone after Feisty upgrade"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by gapplewagen on 2007-04-24
I can't figure this one out.  I just upgraded to Feisty yesterday and most things are working well.  When I boot up, I have sound at login screen and splash screen.  When I first login, mp3/video apps work fine and I get sound.  Then suddenly it's gone.  From AmarokI get:

```

Audio output unavailable; Device is busy
xine parameters:

```

There are no other apps open that would be stealing sound away from Amarok (happens with any other sound app too).  The odd thing is that if I log out I hear the logout sound and then the Ubuntu "drums" for the login screen.  After logging back in (no reboot), sound works fine.  I'm using standard AC97 onboard audio and all worked great under Edgy.  Any ideas?  I'm getting sick of logging out randomly throughout the day :)

---

### Post by hyperair on 2007-04-24
Could you name all the applications you use that output (or input) sound? My guess is that one of these applications is using OSS (Open Sound System) and locks up your sound card so nothing else can get to it.

---

### Post by gapplewagen on 2007-04-24
> **hyperair said:**
> Could you name all the applications you use that output (or input) sound? My guess is that one of these applications is using OSS (Open Sound System) and locks up your sound card so nothing else can get to it.

I really don't use many.  I had Amarok open and was playing some mp3's.  I then paused it for a few hours, came back and browsed the web for a while (no flash or other sound during browsing).  When I tried to unpause Amarok there was no sound.  I just find it odd that during logout it immediately works again.

---

### Post by hyperair on 2007-04-24
Strange. Is your amaroK configured to use ALSA or OSS or what?

---

### Post by gapplewagen on 2007-04-24
> **hyperair said:**
> Strange. Is your amaroK configured to use ALSA or OSS or what?

Under "Engine" in settings I have:

Sound System: xine Engine (my only option)
Output Plugin: Autodetect (what it was in Edgy)

---

### Post by LoCusF on 2007-04-25
I have had similar problems with sound after upgrading to feisty. I have changed the audio output plugin (amarok) to alsa and oss, but get "xine was unable to initialize any audio drivers". I have Ensoniq ES1371 [AudioPCI-97] (rev 08) as my sound card and it has worked just fine until today :) .

---

### Post by hyperair on 2007-04-25
Maybe you could try uninstalling the alsa packages and purging the configuration files with them, then reinstalling alsa..?

---

### Post by frokki on 2007-04-26
Had this same problem today on fresh install of Kubuntu Feisty. Too bad I can't reproduce it, but logging out and back in solved it.

---

### Post by gapplewagen on 2007-04-26
It seems to only affect Amarok and mythtv for me (live tv only, watching other vids or listening to music is fine).  Mythtv reports /dev/dsp is busy even if I have no other sound apps open.  Also odd that it's only when watching live tv in Myth.

---

### Post by gapplewagen on 2007-04-26
I spoke too soon.  I just fired up vlc from a terminal and got this message (and no sound of course)

```

VLC media player 0.8.6 Janus
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[00000336] oss audio output error: cannot open audio device (/dev/dsp)
[00000336] main audio output error: couldn't find a filter for the conversion
[00000336] main audio output error: couldn't create audio output pipeline

```

I'll try removing/purging later.

---

### Post by hyperair on 2007-04-27
@gapplewagen: You're using the OSS driver for some reason or other, and OSS only permits one software to run it at a time. Try 
```

sudo apt-get install alsa-base alsa-utils

```

---

### Post by gapplewagen on 2007-04-27
> **hyperair said:**
> @gapplewagen: You're using the OSS driver for some reason or other, and OSS only permits one software to run it at a time. Try 
```

sudo apt-get install alsa-base alsa-utils

```

Already installed.

```

matt@buster:~$ dpkg -l|grep alsa
ii  alsa-base                                  1.0.13-3ubuntu1                            ALSA driver configuration files
ii  alsa-oss                                   1.0.12-1                                   ALSA wrapper for OSS applications
ii  alsa-utils                                 1.0.13-1ubuntu5                            ALSA utilities
ii  gstreamer0.10-alsa                         0.10.12-0ubuntu1                           GStreamer plugin for ALSA
ii  libesd-alsa0                               0.2.36-3ubuntu4                            Enlightened Sound Daemon (ALSA) - Shared lib
ii  libpt-plugins-alsa                         1.10.3-0ubuntu1                            Portable Windows Library Audio Plugin for th
ii  libsdl1.2debian-alsa                       1.2.11-7ubuntu1                            Simple DirectMedia Layer (with X11 and ALSA 

```

I did just notice that under "System --> Prefs --> Sounds" they were all selected as Autodetect.  I have manually changed them all to Alsa to see if this helps.  Thanks

---

### Post by gapplewagen on 2007-04-27
It looks like making the changes from Autodetect to Alsa did the trick.  Thanks for the help.

---

### Post by KevinColyer on 2007-05-03
I had the same problem with my recent upgrade from Edgy to Feisty. I have resolved it by purging the Network Attached Storage modules ```
sudo dpkg --purge nas nas-bin
``` I think they were  hogging the soundcard preventing alsa from doing its magic. 

I restarted alsa ```
sudo /etc/init.d/alsa-utils restart 
``` and then tested it and it worked. I then restarted the KDE sound service.

Hope this helps. I had NAS installed for LTSP terminals but I had not properly set them up. 

Kevin

---

