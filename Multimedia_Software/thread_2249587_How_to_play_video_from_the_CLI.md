---
title: "How to play video from the CLI?"
date: 2014-10-23
forum: Multimedia Software
---

### Post by jan-banan on 2014-10-23
I have a Raspberry Pi that I can play videos on using omxplayer without entering the desktop. I just boot it up, login to the CLI and run 'omxplayer /path/to/movie' and I want to be able to do this on my laptop. The reason for this is that I want to see how much of a difference it makes on the CPU-usage since I'm trying to optimize video playback. I want to do this in order to limit the CPU usage to keep it as cool as possible since the fan starts running and gets very annoying when I'm watching movies. I have already locked the CPU on the lowest possible clockspeed which helps but some videos stutter so if I could optimize the CPU usage I might gain a few fps.

I have tried running mpv -vo X11 /path/to/movie.mp4 but I got the "[vo] Video output X11 not found!" error message. 
I also tried cvlc /path/to/movie.mp4 but it played an ascii-version of the movie which isn't quite what I want, lol.
I tried mplayer but I got the error message that it failed to set video mode. And it also said: 'FATAL: Cannot initialize video driver' along with several other error messages that I couldn't read since they were rapidly flying over the screen.

The omxplayer is only for Raspberry Pi but a similarly functioning video player for the CLI in Ubuntu would be great, so how can I watch movies from the CLI without using any desktop environment?
XBMC is not an option.

---

### Post by tgalati4 on 2014-10-23
*mplayer* is one of the slimmest video players out there.  Try to capture the error messages (use the scroll lock button) and troubleshoot based on what the errors are.

Using a lower CPU speed means that instructions will get backed up and stuttering will happen.  You want to render the video with your GPU (hardware rendering) if possible, but then the GPU will get hot and probably trigger the fan.  What is the make and model of the laptop?

---

### Post by jan-banan on 2014-10-23
> **tgalati4 said:**
> *mplayer* is one of the slimmest video players out there.  Try to capture the error messages (use the scroll lock button) and troubleshoot based on what the errors are.

Using a lower CPU speed means that instructions will get backed up and stuttering will happen.  You want to render the video with your GPU (hardware rendering) if possible, but then the GPU will get hot and probably trigger the fan.  What is the make and model of the laptop?

Unfortunately I'm not able to capture the error messages using the scroll lock button because I don't have one. 
I have an AMD E300 cpu with an integrated Radeon 6310 gpu, 4gb ram and an old school 500gb harddrive. What I do is I lock the cpu to 780mhz and you'd be surprised how well it works, I can watch 1080p if the bitrate isn't too high. If I allow it to run at the full blazing 1300mhz, full HD is generally no problem at all, that little troglodyte has a few tricks up its sleeve ;)

But I digress...
I tried *sudo* mplayer -vo [fbdev2 and sdl] movie.mp4 which worked except that it stuttered extremely much, if I play it on the desktop it plays fine except that the fan eventually starts whining. So one part of the issue is that I don't have the proper permissions with my normal user (I used tty 6), but what could the other issue be caused by?

---

### Post by tgalati4 on 2014-10-24
The framebuffer device is owned by root.  Presumably this is a security precaution to keep a rogue process from painting your screen.  So you could change the permissions on the framebuffer for this Use Case.

```
sudo chmod 777 /dev/fb0
```

It's hard to watch HD on marginal hardware.

---

