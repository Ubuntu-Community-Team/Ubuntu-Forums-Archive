---
title: "MP3 Playback Not Working"
date: 2010-09-20
forum: Multimedia Software
---

### Post by Vigh on 2010-09-20
Hi I installed restricted extras and mp3 play back was working perfectly for a good time, now just recently it has started to become very choppy, cut in and out and basically make it unbearable to listen to a song. How can I fix this problem?

---

### Post by Vigh on 2010-09-20
I think I may have solved this problem! By turning off visualization, I don't think my intel graphics card can cope with the graphics as well as the mp3 playback! lol!

---

### Post by tommcd on 2010-09-20
> **Vigh said:**
> I think I may have solved this problem! By turning off visualization, I don't think my intel graphics card can cope with the graphics as well as the mp3 playback! lol!
While listening to music run the **top** program from the terminal. Check what processes are using the most CPU cycles while music is playing. If the media player with the visualizations is using a lot of your CPU that may indeed be the problem.

You may also want to consider removing **pulseaudio**. It is a huge resource hog:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273)
All you really need to do to remove pulseaudio is to uninstall *pulseaudio* and *gstreamer0.10-pulseaudio*. Then run *gstreamer-properties* from the terminal and set everything to alsa.

Here is an excellent article that shows you how you can turn pulseaudio on or off as you want in Ubuntu:
[http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7130/1/)

Removing or disabling pulseaudio is optional though. If you are happy with the system the way it is then you could just leave it alone.

---

### Post by r2rX on 2010-09-20
Glad it's working now.

As for PulseAudio, isn't it the future for the sound framework in Linux? I wonder how much software is dependent on PulseAudio a.t.m.

r2rX  :)

---

### Post by Vigh on 2010-09-21
yeah mp3 is working perfect without visualization, however video playback can be choppy at times still, might follow your guide

---

### Post by Vigh on 2010-09-28
seems to have been fixed now, at least on the latest development distribution, was a problem with pulseaudio and flash chewing up too much cpu I think

---

