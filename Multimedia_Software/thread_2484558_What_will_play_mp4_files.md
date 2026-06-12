---
title: "What will play mp4 files?"
date: 2023-03-02
forum: Multimedia Software
---

### Post by lwalper on 2023-03-02
I just tried to play an MP4 video and got the messaqe that I don't have an MP4 decoder. I looked in the SNAP store and found gstreamer codecs, but don't I need some sort of app to install the codecs into?

---

### Post by lwalper on 2023-03-02
I installed VLC from the snap store. It played the video OK, but there was no audio. So ... I uninstalled VLC and installed smplayer using synaptic. Same story -- video played OK, but no audio.

---

### Post by lwalper on 2023-03-02
I have uninstalled smplayer, so, back to my first question. Is there anything that will play mp4 videos?

---

### Post by lwalper on 2023-03-02
It helps to have something plugged into the output jack.:P VLC now working great!

---

### Post by mIk3_08 on 2023-03-02
Totem will play MP4 Video in Ubuntu 22.04 LTS. I have been using totem since the time I have installed Ubuntu 22.04 in my machine. 
Totem is the default video player of 22.04 LTS.
Regards and cheers.

---

### Post by TheFu on 2023-03-02
mp4 is a video container that can have a few different video and audio formats inside.  Basically, saying X won't play mp4 is like saying I can't get water from this 55 gallon drum.  The 55 gallon drum may have water or it might have oil or a few other fluids.  It is just a container, just like .mp4 is a container for different video and audio streams.

VLC and mplayer and mpv should playback any video that you'd want to see ... unless you want pay-per-view files to playback with custom codecs inside.  If you don't hear audio, it is most likely an audio issue on the system, not with those players.

Personally, I've never found any good use for totem or gstreamer.  They are like nano, to be purged for wasting storage.

---

### Post by monkeybrain20122 on 2023-03-03
Did you install ubuntu-restricted-extras? This is the package with all the codecs.

---

### Post by ajgreeny on 2023-03-03
> **lwalper said:**
> It helps to have something plugged into the output jack.:P VLC now working great!
Please tell us in more detail what you mean by this and if it is why you have now marked this as SOLVED, as I do not fully understand what you are saying.

What needs to be plugged in, and into which output jack?

---

### Post by lwalper on 2023-03-03
```
[COLOR=#000000]Did you install ubuntu-restricted-extras? This is the package with all the codecs.[/COLOR]
```
I have now.
```
[COLOR=#000000]Please tell us in more detail what you mean by this and if it is why you have now marked this as SOLVED, as I do not fully understand what you are saying.[/COLOR]

[COLOR=#000000]What needs to be plugged in, and into which output jack?[/COLOR]
```
For some reason my headphones had been unplugged from the audio jack -- hence, there was video, but no audio. The phones were on my head, but silence was the word of the day. When I finally tracked that down, plugged in the headset, then presto!--video AND audio sprang forth from the machine. Thus, problem solved.

---

