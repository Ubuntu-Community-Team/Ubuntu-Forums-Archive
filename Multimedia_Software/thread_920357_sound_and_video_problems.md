---
title: "sound and video problems"
date: 2008-09-15
forum: Multimedia Software
---

### Post by suxxor on 2008-09-15
i`be got the next problem my videos and music on the hard disk can`t run , they just start and blocked their progress i`ve tried to find out what is the problem starting the videos and music through terminal but the terminal doesn`t show any problems , any suggestion what to try

---

### Post by prshah on 2008-09-15
> **suxxor said:**
> i`be got the next problem my videos and music on the hard disk can`t run , they just start and blocked their progress i`ve tried to find out what is the problem starting the videos and music through terminal but the terminal doesn`t show any problems , any suggestion what to try

Firstly, have you installed video/audio support? You can do so by opening the terminal (Applications-Accessories-Terminal) and giving the command ```
sudo apt-get install ubuntu-restricted-extras
``` Note that you will need a live Internet connection for this. (And ensure that using such codecs is not against the law in your country.)

---

### Post by suxxor on 2008-09-15
nope still don`t working maybe i have problems with the hardware `cause i recently put new sound card but i think this is not the problem `cause the same media is running in windows XP installed on the same machine

---

### Post by prshah on 2008-09-16
> **suxxor said:**
> nope still don`t working maybe i have problems with the hardware `cause i recently put new sound card but i think this is not the problem `cause the same media is running in windows XP installed on the same machine

Make up your mind :), is it a hardware problem or not? 

If you still want to continue troublshooting, open System_Preferences_Sound and check the settings there. First, turn everything to Autodetect. Try playing sound/media. Next change everything to ALSA. Try playing sound/media. Next change everything to "PulseAudio Sound Server" (If you have that setting). Try playing sound/media.

If none of the above work, or if you cannot find any of the settings above, post a screenshot of the above window, and also open a terminal (Applications-Accessories-Terminal) and post the output of the below commands```

lspci -v | grep -i -E sound\|multim\|audio
lsmod | grep -i snd
```

---

