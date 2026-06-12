---
title: "After upgrade to 12.04 audio input madly switches between &quot;Line In&quot; and &quot;Mic&quot;"
date: 2012-11-11
forum: Multimedia Software
---

### Post by joelholdsworth on 2012-11-11
Hi,

I just upgraded this Pentium 4 Sony VAIO to 12.04. It has a Realtek ALC260 audio chipset.

After the upgrade the audio output (speakers, or headphones when connected) clicks continuously - like a geiger counter but more regular. If I open the alsamixer, or pavucontrol I can see the problem is caused by the system (PulseAudio, or ALSA - I don't know) madly switching between Mic and Line In, resulting in a series of pops. Adjusting any of the volume controls has no effect on the volume/muting of the pops.

I don't understand why this happens. Maybe this is input sensing gone crazy. Can anyone explain what part of the stack is in control of input selection? maybe that would provide a clue.

Thanks guys
Joel

---

### Post by Jason Spaceman on 2012-11-11
I recently upgraded from 12.04 to 12.10 and I have the exact same problem.  A static-y clicking sound over the speakers and the rapid switching between Line In and Mic.

My audio was fine in 12.04, but ever since the upgrade to 12.10 that clicking sound is constant.  

I know it can't be a hardware problem, as the audio on the same laptop works fine in WinXP.

Does anyone know of a fix?  This is making watching videos and listening to music impossible in Ubuntu.

---

### Post by Jason Spaceman on 2012-11-11
Well I think I might have fixed it after looking at [this thread](http://ubuntuforums.org/showthread.php?t=1979191).

I added a line to the end of /etc/modprobe.d/alsa-base.conf

```
options snd-hda-intel model=generic
```

Then rebooted the laptop and now the audio is fine.  

Most strange, but it works.

---

