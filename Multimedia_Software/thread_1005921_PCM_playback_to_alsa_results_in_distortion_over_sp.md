---
title: "PCM playback to alsa results in distortion over spdif"
date: 2008-12-08
forum: Multimedia Software
---

### Post by crispy_chunks on 2008-12-08
Hello, I have been having this problem for a while now. If I configure playback of audio to be sent to the alsa default (Im not sure what hardware device this is, but it results in sound over spdif, but it is not the spdif device it gets sent to) and the audio is not DTS or AC3 the I get some distortion of the sound. This does not happen when I send the audio (still not talking of DTS or AC3) to the spdif alsa device. You might ask: "why don't you do that then?". Because when I play movies and send non-DTS/AC3 sound to spdif the video-playback for some odd reason plays like 10-15% slower resulting in deeper voices for the actors and slower movements. However pure audio files play at normal speed. This happens with any media/audio player I use so it is a problem, I think, with alsa or the drivers I use for my sound card. An old Aureal A3D card.

A couple of thoughts - the audio, when sent as PCM over spdif gets resampled - at least I think it does. This could be worth looking into, but I lack the knowledge of what to change/try.

Another solution might be to send the audio to some weird device which correctly converts the PCM signal to DTS or AC3.

---

### Post by crispy_chunks on 2008-12-14
Bump

---

### Post by crispy_chunks on 2009-01-06
Badabump!

---

### Post by generica on 2009-01-11
My problem is similar: I can only get non-slowed down PCM to come out of my SPDIF (which is an nVidia Intel-HDA integrated chip, AD1886a) by setting up a ~/.asoundrc that resamples all the PCM data into 44100 hz.  Here is what I set up:

```
pcm.!default {        
        type hw
        card 0
        device 1
        rate 44100
}
```


This worked to get my PCM audio to sound correct when coming out of my SPDIF.

I have a different problem now, which is that after playing a video with DTS encoding via the mplayer -ac hwdts function (which worked correctly), now I can't get ANY PCM audio to come out of my SPDIF at all.  Apparently this problem has something to do with a bug in alsa corrupting the asound.state when an application crashes while sending out PCM audio.  Here is the forum posts I am looking at in relation to this problem (not sure if it is also effecting you):

[http://ubuntuforums.org/archive/index.php/t-388191.html]("http://ubuntuforums.org/archive/index.php/t-388191.html")
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23259.html]("http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23259.html")
[http://ubuntuforums.org/showthread.php?t=445536]("http://ubuntuforums.org/showthread.php?t=445536")

I am still working on troubleshooting this one... time to go digging into asound.state... ugh.

It's worth mentioning that this is not a Ubuntu specific problem, as I am expericing this on my Knoppmyth box with my own complied ALSA as well as the debian stable packages for ALSA. (debian multimedia)

> **crispy_chunks said:**
> Hello, I have been having this problem for a while now. If I configure playback of audio to be sent to the alsa default (Im not sure what hardware device this is, but it results in sound over spdif, but it is not the spdif device it gets sent to) and the audio is not DTS or AC3 the I get some distortion of the sound. This does not happen when I send the audio (still not talking of DTS or AC3) to the spdif alsa device. You might ask: "why don't you do that then?". Because when I play movies and send non-DTS/AC3 sound to spdif the video-playback for some odd reason plays like 10-15% slower resulting in deeper voices for the actors and slower movements. However pure audio files play at normal speed. This happens with any media/audio player I use so it is a problem, I think, with alsa or the drivers I use for my sound card. An old Aureal A3D card.

A couple of thoughts - the audio, when sent as PCM over spdif gets resampled - at least I think it does. This could be worth looking into, but I lack the knowledge of what to change/try.

Another solution might be to send the audio to some weird device which correctly converts the PCM signal to DTS or AC3.

---

### Post by ZMoney on 2009-02-08
> **generica said:**
> 
This worked to get my PCM audio to sound correct when coming out of my SPDIF.

I have a different problem now, which is that after playing a video with DTS encoding via the mplayer -ac hwdts function (which worked correctly), now I can't get ANY PCM audio to come out of my SPDIF at all.  Apparently this problem has something to do with a bug in alsa corrupting the asound.state when an application crashes while sending out PCM audio.  Here is the forum posts I am looking at in relation to this problem (not sure if it is also effecting you):

[http://ubuntuforums.org/archive/index.php/t-388191.html]("http://ubuntuforums.org/archive/index.php/t-388191.html")
[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23259.html]("http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg23259.html")
[http://ubuntuforums.org/showthread.php?t=445536]("http://ubuntuforums.org/showthread.php?t=445536")

I am still working on troubleshooting this one... time to go digging into asound.state... ugh.



This is exactly where I am too.  DTS/5.1 works over SPDIF but no PCM (i.e. mp3s).  I attempted their solution by copying the hex out of their asound.state file that was posted [here]("http://ubuntuforums.org/showpost.php?p=3768828&postcount=5").  It didn't seem to work so I went back to my copy of the asound.state.  I then tried their method of getting the asound.state file from a live cd boot but there was no asound.state file so I don't know.  

I have a ASUS PND-5
lshw says this is my audio hardware:
MCP51 High Definition Audio

SPDIF is going from PC to Onkyo TX604 receiver.  

I think I'm going to try to do the hex change again but I don't think it will work.  

If anyone knows how to fix this please post back.  Perhaps we should start a new thread for this issue as to not hijack this one.

EDIT: found a solution myself.  
1. run gnome-volume-control from terminal
2. goto switches
3. click preferences
4. click IEC985
5. make sure its checked in switches. 

Now both my AC3/DTS and PCM work

---

