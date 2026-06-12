---
title: "sound is like an echo"
date: 2009-08-03
forum: Multimedia Software
---

### Post by crossx14 on 2009-08-03
The sound is slow and like if you are in a tunnel with an echo, delayed. I am also still having choppy vid problems. I made any kind of changes but that did not help.
Any sound played starts to play and then keeps playing that first little part, sometimes forever until I close the application, be this a game such as Lagno, a .wav song, a video, the very login sound, or whatever.
The sound problem makes videos to play too slow, extremely slow, in Totem. A time I could play them right in VLC by setting VLC's audio to alsa instead of pulseaudio, I think (don't remember).
I've tried Ubuntu 7.10, 8.10 and 9. No progress. There is no solution for this issue.
This command:
speaker-test -Dplug:surround51 -c6 -twav
from [http://www.alsa-project.org/main/index.php/SoundcardTesting](http://www.alsa-project.org/main/index.php/SoundcardTesting), for testing 5.1 output, makes a sound plays forever until reboot.
This command:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449), the Comprehensive Sound Problem Solutions Guide, gives an error modprobe: unrecognized option '--purge'
Never a .tar.gz driver o program worked. All of them give some error, permission denied, no such file or directory, etc. However, almost all .deb packages worked fine.
I've tried many things.
The only thing that Ubuntu is good for is for Internet. Not good for Multimedia, Audio, Video. I must download videos and play them in Windows. I had installation problems, audio problems, video capture problems, none solved yet. I still need windows to install Ubuntu, because live cd doesn't boot (could not generate /etc/x11/xorg.conf.failsafe for vesa driver, Squashfs and many other errors). Only Wubi works. Sound Card doesn't work propperly. Modem doesn't work. BT878 video caputre card doesn't work. Usb flashdrive doesn't work. Support doesn't work. Floppy drive only works after typing some strange commands at the console. Never any help solved any of them.
Best regards.

---

### Post by igorzwx on 2009-08-03
"The sound is slow and like if you are in a tunnel with an echo, delayed."

The reason for this is likely to be PulseAudio

Do you have an old box?

I installed OSS4 on my old boxes.
Fantastic sound!

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

