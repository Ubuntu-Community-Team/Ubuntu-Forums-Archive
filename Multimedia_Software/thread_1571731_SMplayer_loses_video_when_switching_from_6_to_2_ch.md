---
title: "S/Mplayer loses video when switching from 6 to 2 channel audio"
date: 2010-09-10
forum: Multimedia Software
---

### Post by adlin5000 on 2010-09-10
This seems to only happen on higher res videos. I'll start a video and if I'm using my headphones, I'll change to 2 channel audio via the audio/channel menu. This causes the video to disappear. Not a blank screen or the logo, no video. The audio continues just fine with 2 channels. Other files play just fine, it only effects that file. Switching back to 6 channel audio has no effect. 

The only way I have been able to restore the video for that file is to open the files.ini and delete the entry for that file. I tried comparing the ini file before and after a change, the only diffrence is the audio line (6 to 2). Changing it back to 6 and restarting that video has no effect.

Now for the tec details. Ubuntu 10.04, kernel 2.6.32-24-generic, 64 bit, mplayer svn:r32007-4.3.4 (compiled using andrew.46's post [HERE]("http://ubuntuforums.org/showthread.php?t=1305181")), SMplayer:0.6.9, Q6600 cpu, and a GeForce 8500 GT.

I'll attach the mplayer and smplayer logs also. [edit] Had to compress the smplayer log, too large.

Thanks for any ideas on this one. Just can seem to figure out how changing the audio would kill the video.

---

