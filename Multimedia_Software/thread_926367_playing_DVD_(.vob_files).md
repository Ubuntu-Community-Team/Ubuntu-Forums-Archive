---
title: "playing DVD (.vob files)"
date: 2008-09-21
forum: Multimedia Software
---

### Post by orengolan on 2008-09-21
I try to play DVD on xubuntu 8.04.
When I insert the DVD I see two folders - VIDEO_TS and AUDIO_TS.
In VIDEO_TS I see a few VOB files. I try to play the bigger one with mplayer (it's an advice I got from someone on irc) and get this error:

mplayer VTS_01_5.VOB 

```
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.60GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing VTS_01_5.VOB.
Seek failed


Exiting... (End of file)
```


Do I need some additional packages to play this type of DVD?
any help will be appreciated!

---

### Post by sukhhari on 2008-09-22
Do a simple thing go to Synaptic Manager and select kaffeine mplayer Install & before play your DVD - reboot your system.

Regards

Harish

---

### Post by orengolan on 2008-09-22
i installed kaffeine but it refuses to open the VOB file.

---

### Post by benerivo on 2008-09-22
You might need to add the medibuntu repositories. See [here]("https://help.ubuntu.com/community/Medibuntu"). Also, how are you trying to launch the .vob from the command line? Make sure you are in the right folder, or just type mplayer and then a space, and then drag the vob in to the terminal.

---

### Post by swoody on 2008-09-23
Have you tried using another media player? I know VLC was awfully easy to get working with DVD's. Just a suggestion if you keep having problems with this :)

---

