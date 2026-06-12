---
title: "Need program to operate and record from comptuer cam"
date: 2020-04-09
forum: Multimedia Software
---

### Post by Autodave on 2020-04-09
Looking fo a program to let me use and record my desktop's camera.

---

### Post by DuckHook on 2020-04-09
[Cheese]("https://wiki.gnome.org/Apps/Cheese") is already installed if you are running a standard Ubuntu Bionic setup. Don't know about Xubuntu though. It's available in the repos in any case.

---

### Post by Autodave on 2020-04-09
That's the one that I was trying to remember.  No, it is not standard on Xubuntu but I remember it from Ubuntu.

Thanks!

---

### Post by DuckHook on 2020-04-09
No prob

---

### Post by TheFu on 2020-04-09
> **Autodave said:**
> Looking fo a program to let me use and record my desktop's camera.

I&#8217;ve never gotten cheese to work, but **simplescreenrecorder** always works for X11 desktops (don't think wayland works). Think it uses a PPA.  There's a recording wizard ...
[LIST]
[*]Choose a window, desktop, rectangle.
[*]Choose the video codec, frame rate, resolution, w/ scaling allowed.
[*]Choose the audio codec, bitrate, other options.
[*]Record
[/LIST]

i routinely capture full screen international sports at 1920x1200, 30fps, h.264, vorbis audio at 160 Kbps. Hours at a time on a Pentium G3258 ($50 CPU in 2016).  The video encoding is set for faster encoding at the price of larger files.  After all the recording is complete, i'll re-encode using a more agreesive handbrake h.264 profile which reduces the file size over 50% and the resolution down to 1080p.  A ryzen 5 does this processing at about 10x realtime.

Just another option for consideration.

---

### Post by Autodave on 2020-04-10
Thanks for the reply!  Cheese works just fine: this is a low res camera and Cheese does just what I need it to do.

---

### Post by TheFu on 2020-04-10
> **Autodave said:**
> Thanks for the reply!  Cheese works just fine: this is a low res camera and Cheese does just what I need it to do.

Ah ... I completely missed the recording from a webcam aspect.

For future lurkers ...

simple-screen-recorder records what's on a screen, not a webcam.  For a webcam, I've used **OBS** [https://obsproject.com/](https://obsproject.com/) , which is a video production system that handles multiple inputs for video, audio, screens, cameras, whatever. It has transition effects like we see on live TV. Definitely overkill for most people.

You could use **ffmpeg** directly to capture /dev/video0 (or 1, 2, 3, 4) and store to a file, transcode, share over the internet, whatever. 
Or use **VLC** for those things.  I've used both ffmpeg and VLC, but ended up using OBS since I needed to mux different video sources into a single "show" to be shared.

---

