---
title: "volume low in smplayer"
date: 2008-05-14
forum: Multimedia Software
---

### Post by pickarooney on 2008-05-14
Simple problem, but I can't find a solution - the volume is very low in smplayer compared to xine, even at max volume. The same is true for amarok, low volume even when set to max. In xine there's a separate setting for AC3 but I can't find an equivalent in smplayer's GUI. In the .ini file for smplayer there is one line with use_hwac3=false but changing this to true causes the video to freeze instantly on playback.

---

### Post by rvm4000 on 2008-05-14
You may try to enable the option "Use software volume control" under Preferences->General->Audio. There you can also set the maximum amplification.

---

### Post by pickarooney on 2008-05-15
> **rvm4000 said:**
> You may try to enable the option "Use software volume control" under Preferences->General->Audio. There you can also set the maximum amplification.

I tried boosting that all the way up to 1000 (no idea what max values are, but t was at 120 to start with) but it made no difference whatsoever unfortunately.

---

### Post by m_yates on 2011-01-27
I know this thread is old, but I stumbled across it searching for a solution to the same problem with smplayer.

In my case, I fixed the low volume problem by switching the output driver from "pulse" to "alsa".

The output driver selection can be found under:

Options>Preferences>General>Audio

Hope this helps anyone else who stumbles across this.

---

### Post by futchy4u on 2011-10-03
options > preference > General > Audio
and then Look for the text box "Max. Amplification" and set it to "1000"
and enjoy :)
BaSSeM

---

