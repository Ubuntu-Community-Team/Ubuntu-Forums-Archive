---
title: "ESS Allegro Not Detected"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by rcoconnell on 2007-03-27
The sound never really worked on my xubuntu install.  The only audio player I could get to work was VLC, and in order to get any sound I had to go to the terminal and run alsamixer.  After doing this, the sound would start up normally.  I've never actually heard the startup noise that xubuntu makes.

I was tinkering today, trying to get songbird to run, and managed to hose the audio completely.  When I tried running my old friend alsamixer, I got
```
alsamixer
          alsamixer: function snd_ctl_open failed for default: No such device
```

Following through the steps in the comprehensive guide, I get:

1. ```
aplay -l
              aplay: device_list:222: no soundcards found
```

2. ```
lspci -v
              00:0d.0 Multimedia audio controller: ESS Technology ES1988 Allegro-1 (rev 12)
                          Subsystem: Delta Electronics Inc Unknown device 0403
                          Flags: medium devsel, IRQ 5
                          I/O ports at 3000 [size=256]
                          Capabilities: <access denied>
```

4.  I did find snd-maestro3, and my /etc/modules now reads
```
lp
fuse
snd-maestro3
```
I can check that this is working.  When I reboot, I get
```
lsmod | grep snd
          snd_maestro3             27523  0
          snd_ac97_codec         97696  1 snd_maestro3
          snd_ac97_bus              3456  1 snd_ac97_codec
          snd_pcm_oss             47360  0
          snd_mixer_oss            19584  0 snd_pcm_oss
          snd_pcm                    84612  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
          snd_timer                   25348  1 snd_pcm
          snd_page_alloc           11400  1 snd_pcm
          snd                           58372  6 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
          soundcore                  11232  1 snd
```

I've also run through
```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
``` a couple of times, and that hasn't helped either.

So, the "Access Denied" in the output of lspci seems telling.  I also seem to be missing some stuff in /dev -- there's no /dev/dsp, or anything like that.  Of course, the complaint seems to be that the device doesn't exist, so I suppose this makes sense.

Any help out there?

-ross

---

### Post by rcoconnell on 2007-03-27
This morning I rembered that the problem arose after installing the gstreamer-alsa package.  Removing it hadn't helped, but installing it again and doing a "complete removal" did.  Whew.

-ross

---

### Post by francisco_athens on 2007-03-30
The Allegro in my Ramline work fine for audio out but I cannot record from the line/mic input.  When I try to bring up the mic level, it slides back down (!), creepy!  It would be handy if the audio recording was of reasonable quality, that is, not recording electrical signals from the logic board or HD ;-) 

Francisco

---

