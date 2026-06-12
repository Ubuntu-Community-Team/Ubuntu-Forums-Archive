---
title: "anyone want to take a stab at getting my audio working"
date: 2009-07-22
forum: Mythbuntu
---

### Post by trevs.bronco on 2009-07-22
here is what he front end log says  happening or not.

```
2009-07-21 21:27:53.021 TV: Attempting to change from None to WatchingLiveTV
2009-07-21 21:27:53.028 Using protocol version 40
2009-07-21 21:27:54.941 DPMS Deactivated 
2009-07-21 21:27:55.783 AFD: Opened codec 0x174a130, id(MPEG2VIDEO) type(Video)
2009-07-21 21:27:55.783 AFD: codec MP2 has 2 channels
2009-07-21 21:27:55.784 AFD: Opened codec 0x488fb80, id(MP2) type(Audio)
2009-07-21 21:27:56.135 Opening audio device 'default'. ch 2(2) sr 48000
2009-07-21 21:27:56.135 Opening ALSA audio device 'default'.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL /dev/mixer
2009-07-21 21:27:56.171 AudioOutput Warning: Mixer attach error -2: No such file or directory
            Check Mixer Name in Setup: '/dev/mixer'
2009-07-21 21:27:56.551 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2009-07-21 21:27:56.692 OSD Theme Dimensions W: 640 H: 480
2009-07-21 21:27:57.284 TV: Changing from None to WatchingLiveTV
2009-07-21 21:27:57.285 Realtime priority would require SUID as root.
2009-07-21 21:27:57.388 Video timing method: USleep with busy wait
2009-07-21 21:28:00.609 NVP: prebuffering pause
2009-07-21 21:28:00.647 RingBuf(myth://192.168.2.2:6543/1029_20090721212752.mpg): Waited 1.0 seconds for data to become available...
2009-07-21 21:28:00.647 Checking to see if there's a new livetv program to switch to..
```

as I was typing this the screen went blank and audio appeared through the analog port and then the screen came back and the audio left, this process repeated for a while then I heard no more audio and the screen still flashed black off and on. i posted this while i could see it and switch computers to finish the post.  

I'm guessing I need to look at /dev/mixer, but the two important questions are how to look at it and what am I looking for? If anyone could point me in the right direction I would really appreciate it.

Thanks in advance,

Trev

---

### Post by ian dobson on 2009-07-22
Hi,

Maybe try setting your audio output device to ALSA:default.

Regards
Ian Dobson

---

### Post by trevs.bronco on 2009-07-23
I have tried ALSA:default and everyother setting in myth frontend setup. as this affects the machine as a whole not just in Myth is there somewhere else I should be going to change settings?

Trev

---

### Post by larsolav on 2009-08-03
Hi, I saw your comment in [this thread]("http://ubuntuforums.org/showthread.php?t=1227173"). Looks like we all have the same motherboard. [My system details are here.]("http://ubuntuforums.org/showpost.php?p=7570755&postcount=215")
I got HDMI audio partially working after the initial setup. All I did was unmute HDMI in alsamixer (did you do that yet?) and in Mythtv i directed in the first line to ALSA:HDMI and then in the second line to ALSA:default (or was it the other way around, can't remember), set the audio to stereo (not 5.1, as that won't work many times, a known bug I believe, but you still get 5.1 sound).
I do not however get audio in mythmusic or outside of MythTV...
Will need to do more configuring for that.

Good luck and Cheers!

---

