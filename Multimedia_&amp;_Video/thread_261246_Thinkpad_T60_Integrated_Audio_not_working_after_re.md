---
title: "Thinkpad T60 Integrated Audio not working after restart"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by adamantivm on 2006-09-20
I appeal to the guidance of the great Linux dieties on this - I hope - relativelly simple issue.

I'm running Ubuntu dapper 6.06 on a Thinkpad T60 (1951-A31). I'm trying to finalize the configuration of the integrated audio card but I can't get it to properly load automatically.

The sympthom that I percieve is that after rebooting, there is no sound even though the driver (snd_hda_intel) is loaded and the mixer controls set properly. What happens is that sound programs get errors while trying to access the card. I'll post another message shortly with a sample of those errors.

Nevertheless, if I close all sound related programs and manually reload the drivers, then everything starts working fine.

So, I guess what I need help on is: how can I troubleshoot whatever is going wrong in the boot process that leaves the card in this non-working state after boot time?

Any tips and advice on where to look would be appreciated.

---

### Post by adamantivm on 2006-09-20
OK, here comes a little bit more data, in case it helps.

Here's an example of what happens when I try to play a sound file right after reboot:

```

julian@zapatilla:~$ mplayer /usr/lib/openoffice/share/gallery/sounds/wallewal.wav
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel  (Family: 6, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
....
Playing /usr/lib/openoffice/share/gallery/sounds/wallewal.wav.
Audio file file format detected.
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 11025 Hz, 1 ch, s16le, 176.4 kbit/100.00% (ratio: 22050->22050)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
Building audio filter chain for 11025Hz/1ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
ALSA lib pcm_direct.c:786:(snd_pcm_direct_initialize_slave) snd_pcm_hw_params_any failed
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to initialize slave
alsa-init: playback open error: Invalid argument
[AO OSS] Can't set audio device /dev/dsp to s16le output, trying s16le...
[AO OSS] Can't set audio device /dev/dsp to s16le output, trying s16le...
[AO OSS] Can't set audio device /dev/dsp to s16le output, trying s16le...
[AO OSS] Can't set audio device /dev/dsp to s16le output, trying s16le...
[AO OSS] Can't set audio device /dev/dsp to s16le output, trying s16le...
(continues until ^C)

```

This might give a little bit more info about which exact audio device I have on my T60:

```

julian@zapatilla:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

julian@zapatilla:~$ lspci -vv | grep Audio
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

I couldn't find any relevant information in dmesg or /var/log/messages.

Finally, this is what I do each time to get sound working again:

```

julian@zapatilla:~$ lsmod | grep snd | cut -d' ' -f1 | xargs -n 1 sudo rmmod
julian@zapatilla:~$ sudo modprobe snd_hda_intel

```

Any hints on how to configure my sound card so that the drivers would be loaded properly on startup with be greatly appreciated.

---

### Post by adamantivm on 2006-09-21
Anybody? Any hints as to how to debug the driver loading process during boot so I can figure out what is different when I load them by hand?

Thanks.

---

### Post by akvik on 2006-10-23
Do this actually mean that by the commands:
```

julian@zapatilla:~$ lsmod | grep snd | cut -d' ' -f1 | xargs -n 1 sudo rmmod
julian@zapatilla:~$ sudo modprobe snd_hda_intel

```

..you get it working again? 

I have the same hardware, but my sound doesn't work at all. I tried the first command, with the following output:
```
~$ lsmod | grep snd | cut -d' ' -f1 | xargs -n 1 sudo rmmod
ERROR: Module snd_hda_intel is in use
ERROR: Module snd_hda_codec is in use by snd_hda_intel
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_hda_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_intel,snd_hda_codec,snd_pcm,snd_timer
ERROR: Module soundcore is in use by snd
ERROR: Module snd_page_alloc is in use by snd_hda_intel,snd_pcm

```

Could you tell me what to do to get it working? 

:-)

---

### Post by akvik on 2006-10-23
Thanks!

You solved it for me! By removing the modules and modprobing snd-hda-intel sound works again! 

There must be a way to load the modules the right way by using the blacklists or something. But as long as I can do this:
```

# sudo /etc/init.d/alsa-utils stop

# sudo /etc/init.d/alsabase stop

# modprobe snd-hda-intel

```

..then I'm happy!

---

### Post by adamantivm on 2006-10-24
akvik

I'm glad you got your sound working too.

What I typically do is to reload the sound first thing when I boot up my thinkpad, even before logging in to X. Then, I don't restart my thinkpad in a very long time - almost always suspend/resume instead.

I still haven't figured out how to get the proper loading automatically at system startup. If you figure something out, please let me know.

---

### Post by akvik on 2006-10-24
How about blacklisting the modules, and then modprobe in the startup script? Havent't tried it, I also suspend the computer instead. But it should work, even though it's not that elegant...

---

### Post by anmar on 2006-10-30
Ok... the guys on #ubuntu irc channel asked me to enable my internal modem in the BIOS, which was disabled.  When I restarted the machine and opened my volume manager in GNOME, I had to unmute everything and increase the PCM volume. Sound works perfectly now.

Hope this helps most of you guys.

BTW, I have a Lenovo 3000 N100 with core duo and:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

chipset.

Hope this helps,

Anmar

---

