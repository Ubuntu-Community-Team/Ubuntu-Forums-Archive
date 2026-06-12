---
title: "Audio working on headphones but not speakers"
date: 2009-08-02
forum: Multimedia Software
---

### Post by tompe on 2009-08-02
I have tried almost everything already and would really appreciate it if someone could help me. 

My laptop is an HP dv5-1251nr

I am not sure how to check the exact type of sound card I have. The few times I have checked it said either Intel HDA or IDT.

Thanks in advance

---

### Post by igorzwx on 2009-08-03
commands (on Terminal)

aplay -l

lspci -v

lspci > hardwareinfo.txt


The last command will produce a text file " hardwareinfo.txt"


Install several Ubuntu 9.04 on the same box

try:

1. ALSA + esound (without pulseaudio)

2. OSS4 (without alsa and pulse)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

one of these solutions may work


**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

