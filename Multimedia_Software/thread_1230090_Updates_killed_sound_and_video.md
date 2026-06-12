---
title: "Updates killed sound and video"
date: 2009-08-03
forum: Multimedia Software
---

### Post by dkolars on 2009-08-03
Just installed some "critical updates" yesterday into Ubuntu 9.04.  Now, i have ONLY the log-on sound... cannot play audio files (any type), and what's just as bad, my video playback has gone away as well... Again, all file types...  The videos will open, but play at 2-3 frames a second, with no sound.

I've spent the bulk of the evening on the i-net searching newsgroups, and have uninstalled, re-installed, etc. and have had NO luck, other than bad, of course...

UB sees the sound card:

~dkolars@Desktop:~$ aplay -l
~**** List of PLAYBACK Hardware Devices ****
~card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
~ Subdevices: 0/1
~Subdevice #0: subdevice #0

and tells me I'm a user:

~dkolars@Desktop:~$ grep 'audio' /etc/group
~audio:x:29:pulse,root,dkolars

Don't know what 'pulse' is...

Sound card is HDA Intel ALC88 -- video card is NVIDIA GeForce 8600GT.

Everything worked JUST FINE until I did the "critical updates"...  I'm not sure I like the definition of "critical" that is being used here...

---

### Post by dkolars on 2009-08-03
OK, so I posted this, and again tried to open a video, and it works!  ???  .flv, .wmv, etc. all play now...  This is making no sense at all, but I'll take it!!

---

### Post by vinutux on 2009-08-03
Check if you are enable any thirdparty repos like mediubuntu...

Application>Administration>Synaptic>setting>repositories >third-party software tab ....and disable that repos...reload and reinstall codecs [ubuntu-restricted-extras]

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

