---
title: "kdenlive: computer shut-down during render"
date: 2013-01-18
forum: Multimedia Software
---

### Post by cinnamonspider on 2013-01-18
I recently started using kdenlive, and it's been working just fine, until I finished the video that is.
First I tried rendering the whole project - the video wasn't even that long, around 2 minutes - but halfway through the rendering process, the computer just shut down completely.
After that I tried rendering a few clips of the video at a time, which seems to work as long as the rendering process doesn't take longer than 4-5 minutes, and even then it only works sometimes.

Any help would be much appreciated.

---

### Post by c2tarun on 2013-01-18
> **cinnamonspider said:**
>  which seems to work as long as the rendering process doesn't take longer than 4-5 minutes, and even then it only works sometimes.

Any help would be much appreciated.

Can you please elaborate it little bit.

---

### Post by Thee on 2013-01-18
Maybe your CPU is overheating while rendering and its shutting down to prevent CPU damage.
Is there anything else CPU intensive that you can run to check if the same thing happens? Maybe a game?

---

### Post by dannyboy79 on 2013-01-18
i was going to say the same thing, sounds like an overheating issue. i would take it outside and blow out the case with air can and make sure there's no dust clogging the fan vents etc etc.

see if you can view temps while you're rendering to see how hot it's getting. Where did you get kdenlive from? I use sunab's kdenlive-svn ppa and medibuntu repo for the "extra's" libraries for ffmpeg. i am using xubuntu 12.04

---

### Post by cinnamonspider on 2013-01-18
I don't think it's an overheating issue, since it never shuts down like that even if I'm running several different programs and applications simultaneously. It only happens while rendering (during which I make sure not to have anything else running, though it doesn't seem to matter). 

As for where I got kdenlive from, I just downloaded it via the software center.

---

### Post by dannyboy79 on 2013-01-18
that's a very old version, i would suggest you try a more recent release of it. first remove kdenlive, melt or mlt, and frei0r-plugins.

then enable the stable ppa from sunab, just google "sunab's kdenlive-release ppa"
then install that, you'll also want to enable the mythbuntu repository for the libavformat-extras-53 libraries or whatever they are and for the better ffmpeg.

i am using xubuntu 12.04 and using sunab's svn ppa for kdenlive and have no issuse at all, it works great and can render to h264/aac mp4 files.

---

### Post by Thee on 2013-01-19
I'm still not sure how or why would a software bug or what ever it is, completely shutdown the computer. That sounds like a hardware problem and nothing else. But, try the new release like dannyboy79 suggested and if the problem solves, great.

---

### Post by cinnamonspider on 2013-01-21
I installed the new release as suggested, but the problem still remains.

---

### Post by dannyboy79 on 2013-01-21
are you positive this is related to kdenlive? have you tried to open tons of other apps to attempt to crash your system? open like 100 tabs in google chrome or firefox, run a bunch of other apps.

I don't really know what to suggest as I don't have any issues. Maybe try the kdenlive forums if you feel it's related to kdenlive

---

### Post by cinnamonspider on 2013-01-21
Well, since the only time the problem occurs is when I'm trying to render, and I already know that I can run tons of other apps simultaneously without the computer shutting down, it's really the only logical conclusion.

Alright, I'll see if I can find a solution there, then. Thanks for all your suggestions, though.

---

### Post by dannyboy79 on 2013-01-22
yeah, i am trying thats for sure. lol
have you tried to start kdenlive from the command line, have the terminal open and visible right as you click render to see if there are any messages in the terminal window?

---

### Post by Thee on 2013-01-22
Or how about this, since it only happens when you render, get some other video editor and try rendering from there too and see what happens.

---

### Post by dannyboy79 on 2013-01-22
OR, you could just take a video file and try to re-encode it using either handbrake or avidemux. maybe it's a ffmpeg issue or maybe even melt. melt is the framework behind kdenlive. BUT my melt works fine from sunab's svn ppa. so not sure. are you using medibuntu repos for the extra ffmpeg libs?

---

### Post by cinnamonspider on 2013-01-27
Tried your suggestion of starting kdenlive from the command line, but there were no messages in the terminal window.
I am using medibuntu repos, and melt works fine for me as well.

As for trying a different video editor, I couldn't install OpenShot for some reason, and I haven't been able to find another editor that seems like it would work well enough.

---

### Post by dannyboy79 on 2013-01-27
i am out of suggestions. did you post over at the kdenlive forums?

---

### Post by FakeOutdoorsman on 2013-01-28
Video encoding is very CPU intensive; probably more so than anything else you're doing, so I recommend revisiting the probability of overheating. You can try using ffmpeg by itself the test this theory:

```
ffmpeg -f lavfi -i mandelbrot=s=1280x720 -t 00:05:00 -c:v libx264 -preset veryslow -crf 18 -pix_fmt yuv420p output.mkv
```

This will create a Mandelbrot set and encode it with x264 using a slow encoding preset resulting in a 5 minute long output.

You will have to [compile ffmpeg](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), use [Jon Severinsson's ffmpeg PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), or use a simple [static build](https://ffmpeg.org/download.html#LinuxBuilds) if you want to try this. I doubt the fake "ffmpeg" from the repo has the Mandelbrot video source.

---

### Post by saeon on 2013-10-09
Hey guys, im loving the linux experience as a new user and cannot tolerate the thought of returning to windows, but i have the same problem of CPU crash during video render, and i can assure you is an overheating issue in my case anyway. I've exhausted many paths to be here now with this confirmation, including reinstalling mint, installing lowlatency, and have arrived at ubuntu studio 12.04. I have a quad core, 32 bit, with 2gig ram.

From observing system monitors, i can say that CPU is completely redlined at the start of rendering, until the pc switches off suddenly a few minutes later. i dont know how to find CPU thermometer and so i just opened the box and touched the heat dissipator - VERY hot!

This problem occurs with all the video editors i found and tested, about 6 diffrent ones. i'd also like to make another observation.

in windows, i could render fine as long as i rendered one video at a time. i also found the rendering process to be helluva faster than any linux app - like ten times at least! in windows i used sony vegas, but since i never used its features, i ended up with wondershare for simplicity... this is cool, but since i dont really want to go back to windows at all, maybe there are methods of tweaking i could apply. 

i dont know too much about terminal, but i did mess about with ulimit in mint 15 and found that an extension of available memory from 64 to 1024 did buy alot more rendering time and ease pressure on the CPUs, altho it did eventually overheat again. i also found that the rendering process used no more than 700meg of memory in its task.

Thank you for any help you might have for me, i really appreciate it, as im not sure what to do from here... thanks

---

### Post by saeon on 2013-10-09
okay so i've found a quickfix for now... a small app called cpulimiter... now searching for a less manual method of limiting CPU access for the desired rendering program...

---

### Post by FakeOutdoorsman on 2013-10-09
> **saeon said:**
> in windows, i could render fine as long as i rendered one video at a time. i also found the rendering process to be helluva faster than any linux app - like ten times at least!
There are many variables to explain the differences. I've found the opposite: that Windows is generally slower when all of the other factors are the same or similar.

> **saeon said:**
> okay so i've found a quickfix for now... a small app called cpulimiter... now searching for a less manual method of limiting CPU access for the desired rendering program...
Alternatively you can see if "[nice](http://en.wikipedia.org/wiki/Nice_%28Unix%29)" helps:
```
nice ffmpeg -i input.avi output.mp4
```
You could also use it for GUI programs, but note that kdenlive uses ffmpeg to encode, so you'll probably have to add nice to the ffmpeg presets in kdenlive.

---

