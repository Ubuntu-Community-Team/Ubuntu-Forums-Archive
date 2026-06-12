---
title: "Intermittent VMWare sound problems"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by xp_newbie on 2007-01-04
I know that this problem has been reported before, but no posting that I read suggests a real or methodic (final) solution to the problem.

The sound on my Ubuntu system works perfectly.

When I start a Windows 2000/XP VM on VMWare, the sound works there too - **most** of the time. I almost always make sure that when I start VMWare nothing else is being played (sound-wise) on the Ubuntu system.

But every once in a while, despite the sound device not being used at all by any Linux program (or so I think), I get the following error message when I start a Windows 2000/XP VM on VMWare:

> Failed to open sound device /dev/dsp: Device or resource busy Virtual device sound will start disconnected.

This is baffling since I have no idea what prompts this kind of **inconsistent** behavior. Also, the only way to get out of this situation is to reboot the Ubuntu system completely :(.

I found [this posting]("http://www.ubuntuforums.org/showthread.php?t=279863&highlight=VMWare+Failed+to+open+sound+device+%2Fdev%2Fdsp") which seems to describe a similar case to mine, but it ends without a real working solution.

It seems hard to believe that this problem has no fix since there must be many users annoyed by this and since VMWare is a productivity tool for power users who are usually annoyed by "glitches" like this. Any idea whether there is a permanent fix or workaround to this problem?

BTW, my sound device (according to Device Manager) is a 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller. Under it there is a list of both ALSA and OSS devices:

> ALSA Capture Device
MIC ADC ALSA Capture Device
MIC2 ADC ALSA Capture Device
ADC2 ALSA Capture Device
ALSA Control Device
ALSA Playback Device
IEC958 ALSA Playback Device
OSS Control Device
OSS PCM Device
OSS PCM Device
OSS PCM Device


Thanks!
Alex

---

### Post by xp_newbie on 2007-01-04
OK - problem solved. Here is how I did it:


[LIST=1]
[*]sudo -i
[*]aptitude install alsa-oss
[*]chmod +s /usr/lib/libaoss.so.*
[*]mv /usr/bin/vmware /usr/bin/vmware.orig
[*]echo '#!/bin/bash' > /usr/bin/vmware
[*]echo 'LD_PRELOAD=libaoss.so exec /usr/bin/vmware.orig "$@"' >> /usr/bin/vmware
[*]chmod +x /usr/bin/vmware
[*]exit
[/LIST]

(now launch vmware as before)

Tested on VMware version 5.5.3 build-34685.

It is time to give back to this wonderful community, so I will post this in the HOWTO forum as well.

Alex

---

### Post by puccaso on 2007-01-13
i did this
and it messed up vmplayer for me
i cannot use this commant
it says something about logs and that my file size has changed

---

