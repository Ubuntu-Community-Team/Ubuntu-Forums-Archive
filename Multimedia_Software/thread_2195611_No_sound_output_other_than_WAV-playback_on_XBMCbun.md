---
title: "No sound output other than WAV-playback on XBMCbuntu (Ubuntu 11.10 + XBMC Frodo 12.2)"
date: 2013-12-25
forum: Multimedia Software
---

### Post by dennis-binkhorst on 2013-12-25
Hi,

I have been doing a fresh install of XBMCbuntu 11 (Eden) and upgraded XBMC to Frodo.
Audio output is configured to Analog, 2.0. No pulseaudio installed.

On audio playback (mp3-streams, mp3 (vbr/cbr), ogg-vorbis) I get no error from XBMC, but I hear no sound.
So I fiddled with the Audio output device settings, but this unfortunately none resulted in sound output.

When running```
 aplay /usr/share/sounds/alsa/Front_Center.wav
``` from terminal I do get sound output from my speaker.
Playing[FONT=courier new] /usr/share/sounds/alsa/Front_Center.wav[/FONT] from XBMC also results in sound output.

From the above findings, I conclude my sound card installed correctly and my Audio Output Settings in XBMC are also configured correctly.

Any suggestions on how to get sound output of other audio formats running?

Thanks in advance!

---

### Post by dennis-binkhorst on 2013-12-26
So, after finding a ticket at xbmc.org regarding a similar (if not exactly the same!) issue in a ticket at [http://trac.xbmc.org/ticket/13949](http://trac.xbmc.org/ticket/13949), i got a workaround.

I added the following to [FONT=courier new]~/.xbmc/userdata/advancedsettings.xml[/FONT] (text in bold), as recommended in the above mentioned ticket.

```
<advancedsettings>
  <useddsfanart>true</useddsfanart>
  <cputempcommand>cputemp</cputempcommand>
  <gputempcommand>gputemp</gputempcommand>
  <samba>
    <clienttimeout>30</clienttimeout>
  </samba>
  <network>
    <disableipv6>true</disableipv6>
  </network>
[COLOR=#ff8c00][B]  <audio>
    <resample>48000</resample>
  </audio>[/B][/COLOR]
</advancedsettings>
```

This got my sound in XBMCbuntu working again for mp3- and ogg playback.
However, a comment on [http://forum.xbmc.org/showthread.php?tid=137110&pid=1159656#pid1159656](http://forum.xbmc.org/showthread.php?tid=137110&pid=1159656#pid1159656) indicates that upsampling isn't the best thing to do, and it is recommended that if possible, to 'get around' upsampling.

Is there a way to a prettier solution to this problem?

The used audio device is an **iec958**:
(note that[FONT=courier new] card 0[/FONT] is part of an ATI HD3450 AGP card, with a DVI port, so no HDMI connector)

```
mxadmin@ks022-02m:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Thanks again!

---

