---
title: "Sound Issues, ALSA problems?"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by TheIdiotThatIsMe on 2006-01-19
Sorry for recreating this thread, the original died out days ago and I've been very frustrated at trying to fix these problems.

I have read through many threads dealing with users having sounds issues in games, and have yet to be able receive sound in some games.

I currently have a SoundBlaster Live! 24-Bit soundcard. Under Multimedia System Selector I have OSS for both input and output, if I choose anything else I lose all my sound. I've read that my card should support ALSA, but when I try to choose ALSA and click test (on either input or output) I receive the error: Failed to construct test pipeline for 'ALSA - Advanced Linux Sound Architecture'. 

I get sound from my music programs and some games, such as Quake IV's demo. However, I do not currently get sound from Enemy Territory and LinCity-NG.

For LinCity-NG I get the following terminal output: 

```
Starting lincity-ng (version 1.0.1)...
[/home/anthony/.lincity] is in the search path.
[/home/anthony/.local/share/lincity-ng] is in the search path.
LINCITY_HOME: /home/anthony/.local/share/lincity-ng
open /dev/sequencer: No such file or directory
OpenGL Mode 1024x768
ERROR of degree -1:Error. Can't find LINCITY_HOME
anthony@ubuntu:~$
```

If I do a sudo modprobe snd-seq I get sound. Is there anyone to get around this or load the module on startup?

For Enemy Territory, I get the following error on sound in the terminal output:

```

------- sound initialization -------
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
```

I dont really know what that means :confused: But I know I've seen it and still cant figure out how to fix it.

---

### Post by TheIdiotThatIsMe on 2006-01-21
No ideas on the problem with ALSA? :???:

---

### Post by TheIdiotThatIsMe on 2006-01-26
Sorry for bringing back the thread, I still have not been able to fix the sound problems :(

---

### Post by christhemonkey on 2006-01-26
to load modules at boot, place them in the "/etc/modules" file
sudo gedit /etc/modules
and place your snd-seq in there.

---

### Post by TheIdiotThatIsMe on 2006-01-26
[QUOTE=christhemonkey]to load modules at boot, place them in the "/etc/modules" file
sudo gedit /etc/modules
and place your snd-seq in there.[/QUOTE]

Thanks, that's one problem down :D

---

### Post by christhemonkey on 2006-01-26
Glad i can help!
I also occasionally get this problem with broken pipelines, but always only for recording...

---

### Post by TheIdiotThatIsMe on 2006-01-26
[QUOTE=christhemonkey]Glad i can help!
I also occasionally get this problem with broken pipelines, but always only for recording...[/QUOTE]

Unfortunately mine's not just recording, but whenever I try to test it...

---

### Post by christhemonkey on 2006-01-28
this site looks like it will be really helpful, though havent got round to doing anything they say yet!
[www.ubuntustudio.com]("www.ubuntustudio.com")

---

