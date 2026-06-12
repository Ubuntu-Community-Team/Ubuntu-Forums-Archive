---
title: "NForce2 and PulseAudio"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by ShishKabab on 2007-11-29
Hi all,

I just installed the nForce2 drivers following [these]("http://ubuntuforums.org/showthread.php?t=253725") instructions. Then I installed PulseAdio.
Then I got the following error when I did amixer -Dpulse:
ALSA lib control.c:874: (snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so
Then I searched a little bit around and they said you have to install libasound2-plugins. When I now do amixer -Dpulse, there's no output.

When I do aplay /usr/share/sounds/alsa/Front_Center.wav it fails:
```

vincent@vincent-desktop:~$ sudo aplay /usr/share/sounds/alsa/Front_Center.wav
Playing WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
*** PULSEAUDIO: Unable to create stream.
aplay: set_params:961: Unable to install hw params:
... Some info about the WAV file here ...

```

Also Skype(which uses ALSA) and Flash in Firefox(which also uses ALSA) crashes. Skype with a failed ASSERT on sign in: 
```

ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL puls
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL puls
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL puls
*** PULSEAUDIO: Unable to create stream.
skype: pcm_pulse.c:112: pulse_stop: Assertion `pcm->stream' failed.
Aborted (core dumped)

```

Any suggestions?

Kind Regards,
Vincent

---

### Post by ShishKabab on 2007-12-04
Anyone?

---

### Post by fozner on 2007-12-07
Pulseaudio does this on Fedora 8 sometimes when xmms crashes and suddenly no input or output devices show up in padevchooser or paman.  Killing the pulseaudio daemon with pulseaudio -k && pulseaudio -D doesn't fix it either and seems to be killing X and logging in again.

In your case, it may be that the alsa devices aren't being detected.  You may have to go through the steps of configuring pulseaudio manually following the instructions on the pulseaudio site. [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

I had this problem (on a different machine) and what I did was I looked at the output of aplay:
alias g='grep -i'
aplay -l|g card
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]

Card 0 and device 0 translates to hw:0,0 in ALSA speak but for some reason hw:0,0 didn't work so I had to put plughw:0,0 into my /etc/pulse/default.pa , created devices called input and output. I guess there are bugs in the device detection yet.

---

### Post by ShishKabab on 2008-01-23
Mmm.... The command 'aplay -l' gives this output:
```
**** List of PLAYBACK Hardware Devices ****
aplay: device_list:225: snd_ctl_pcm_next_device
```

This probably means that my NForce2 sound card isn't detected by ALSA now that I installed the drivers. OSS still detects them correctly. Is there any way to make ALSA detect the sound cards?

Greetz,
Vincent

---

### Post by jocko on 2008-01-24
> **ShishKabab said:**
> Mmm.... The command 'aplay -l' gives this output:
```
**** List of PLAYBACK Hardware Devices ****
aplay: device_list:225: snd_ctl_pcm_next_device
```This probably means that my NForce2 sound card isn't detected by ALSA now that I installed the drivers. OSS still detects them correctly. Is there any way to make ALSA detect the sound cards?

Greetz,
Vincent

nvsound are oss drivers, they don't support alsa so to get them working the alsa drivers have to be unloaded and blacklisted. use oss instead.
I also had some problems setting up pulseaudio, but I managed to get it working after some tinkering. [This post]("http://ubuntuforums.org/showpost.php?p=4186539&postcount=177") may help you.

---

