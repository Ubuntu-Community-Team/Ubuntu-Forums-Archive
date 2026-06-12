---
title: "disable sound device"
date: 2008-05-24
forum: Multimedia Software
---

### Post by teust on 2008-05-24
Hi,

I recently installed ubuntu Hardy Heron.  I have a creative SB x-fi soundcard so I used this guide to install drivers, [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2).  Everything went well but no sound or so I thought.  On running osstest in the terminal I do get sound, it seems to be picking up two sound devices and is defaulting to the non SB x-fi.  Here's the output from osstest, I only get sound for the second device /dev/oss/sbxfi0/pcm0 and no sound for /dev/oss/hdaudio0/pcm3. Can I disable the device somewhere?  When I launch ossxmixer I get these two devices showing up also.

```

*** Scanning sound adapter #-1 ***
/dev/oss/hdaudio0/pcm0 (audio engine 0): HD Audio front
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47989.00 Hz (-0.02%)> 
/dev/oss/hdaudio0/pcm1 (audio engine 1): HD Audio center/LFE
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47976.00 Hz (-0.05%)> 
/dev/oss/hdaudio0/pcm2 (audio engine 2): HD Audio rear
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47979.00 Hz (-0.04%)> 
/dev/oss/hdaudio0/pcm3 (audio engine 3): HD Audio side
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47976.00 Hz (-0.05%)> 
/dev/oss/hdaudio0/spdout0 (audio engine 4): HD Audio spdif-out
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47976.00 Hz (-0.05%)> 
/dev/oss/hdaudio0/pcmin0 (audio engine 5): High Definition Audio rec1
- Skipping input only device
/dev/oss/hdaudio0/pcmin1 (audio engine 6): High Definition Audio rec2
- Skipping input only device
/dev/oss/hdaudio0/pcmin2 (audio engine 7): High Definition Audio rec3
- Skipping input only device

*** Scanning sound adapter #1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 8): Sound Blaster X-Fi output
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47510.00 Hz (-1.02%)> 
/dev/oss/sbxfi0/pcmin0 (audio engine 9): Sound Blaster X-Fi input
- Skipping input only device

*** All tests completed OK ***


```

Thanks
T

---

