---
title: "Dell M1530 Sound Recording"
date: 2009-08-03
forum: Multimedia Software
---

### Post by Lacrimstein on 2009-08-03
I have a problem with my built-in microphone since I installed Jaunty: it records at extremely low volume levels. I have tried everything: pavucontrol (which raised the volume, but added crackle which made my voice uncomprehensable), messing with sound settings, alsamixer, etc. Can anyone help me?

---

### Post by igorzwx on 2009-08-03
install several Ubuntu 9.04 on the same box

try:

1. ALSA + esound (without pulseaudio)

2. OSS4 (without alsa and pulse)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

one of these solutions may work


**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document. 
 
[B]
[/B]

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

