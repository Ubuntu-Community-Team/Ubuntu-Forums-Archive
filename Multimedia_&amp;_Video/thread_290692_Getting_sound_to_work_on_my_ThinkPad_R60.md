---
title: "Getting sound to work on my ThinkPad R60"
date: 2006-11-01
forum: Multimedia &amp; Video
---

### Post by AlucardZero on 2006-11-01
Hi,

I'm having a hell of a time getting sound to work on my Lenovo Thinkpad R60 running Edgy.  It did not work upon fresh install of Edgy, nor on fresh install of Dapper, nor after the dist-upgrade to Edgy (I'm currently on a 12-hour old fresh install of Edgy, with the default (I think) 2.6.17-10-generic kernel).  It *did* work in Windows.

I've gone through the Comprehensive Sound Problem Solutions Guide thread; purging the packages and reinstalling them didn't work.  In the process of all this, I also tried compiling the latest alsa packages from source, following [this guide](http://www.alsa-project.org/alsa-doc/doc-php/template.php?module=hda-intel).  It didn't work, and I have not done that on this install.


aplay -l gives me```
alucard@solo:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``` so I beleive the card is being detected.

I've played with alsamixer and all the volume and mute buttons I can find, to no avail.

Totem refuses to even try to play files; it "opens" them, but when Play is clicked, the position slider doesn't move. I have a .ogg, .mp3, .wav, and .midi to test with. VLC will at least pretend to be playing it, but no sound comes out.

In Sound Preferences, I have everything on Auto (the default), and when I click a Test button I get: ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not negotiate format
```.

And when I try mpg123, I get output that might be more helpful:```
Playing MPEG stream from 12 stones - crash.mp3 ...
MPEG 1.0 layer III, 192 kbit/s, 44100 Hz stereo
ALSA lib pcm_direct.c:867:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:876:(snd_pcm_dmix_open) unable to initialize slave
ALSA snd_pcm_open error: Invalid argument
libao - OSS cannot set channels to 2
ALSA lib pcm_direct.c:867:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:876:(snd_pcm_dmix_open) unable to initialize slave
Creating link /root/.kde/socket-solo.
can't create mcop directory
```(This is actually further than I've gotton with mpg123 before; usually it was "No supported rate found!" or "Couldn't open default sound device")

Thank you for your time helping me with this.  If you need any more information don't hesitate to ask.

---

### Post by tishioka on 2006-11-01
G'day, 
Don't want to be hijacking this thread, though I too am having the exact same problem with my Toshiba Sat M100. I have tried the same things which brought me to the same outcome... 
PLEASE HELP!

---

### Post by AlucardZero on 2006-11-02
[http://ubuntuforums.org/showthread.php?p=1653926](http://ubuntuforums.org/showthread.php?p=1653926)

That fixed it for me.

Jesus christ, that was too hard.

Edit:  Even easier than that, as in [this post](http://ubuntuforums.org/showpost.php?p=1686685&postcount=8), if I re-enable the modem in my BIOS, sound works fine.

---

