---
title: "choppy video and audio in ubuntu"
date: 2009-01-20
forum: Multimedia Software
---

### Post by ksheyman on 2009-01-20
Hello, I am extremely new to linux so please be gentle. I just switched my laptop over to ubuntu and I'm having trouble with video and audio playback. When playing videos it actually plays in slow-motion, super choppy and unwatchable. It's the same no matter what size I play the video. The audio is the same way, even the startup sound is choppy. I am using the correct drivers for the video card, I made sure of that. This was not a problem with windows although the video card does really really suck. Any ideas? Please give me step-by-step for any suggestions because I guarantee I won't know what you're talking about!! Thanks!!!!!!

---

### Post by overdrank on 2009-01-20
> **ksheyman said:**
> Hello, I am extremely new to linux so please be gentle. I just switched my laptop over to ubuntu and I'm having trouble with video and audio playback. When playing videos it actually plays in slow-motion, super choppy and unwatchable. It's the same no matter what size I play the video. The audio is the same way, even the startup sound is choppy. I am using the correct drivers for the video card, I made sure of that. This was not a problem with windows although the video card does really really suck. Any ideas? Please give me step-by-step for any suggestions because I guarantee I won't know what you're talking about!! Thanks!!!!!!

Hi and welcome, some info that may help us.
What is the model of the graphics card, and some system specs.
The version of ubuntu you are using and have you installed the [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by ksheyman on 2009-01-20
Hello there. One update first off, I restarted the system and the audio problem went away. However the problem still exists with the video. When playing in anything but a small window the framerate drops down to literally 2-3 fps. Another wierd thing is that whenever I open a new video or skip ahead in a video, it takes several seconds with just the audio playing before it appears. I have installed the proprietary ATI drivers. The video card is an ATI Radeon Xpress 200 (real piece of junk, but it worked fine with windows for video playback). The audio card is a Realtek ALC861 but since it seems to be working fine now I guess that doesn't matter. I am using Ubuntu 8.10. At first I thought that the video card must just be overworked with the multiple workspace feature (which is awesome), but it reacts the exact same way when I reduce my workspaces to one. I remember this probelm did exist sometimes in windows IF i was using multiple monitors and running a lot of programs at once. However if the video player was the only thing running it worked fine. One other thing that may be useful - when I am playing a video the CPU usage goes way up. It was at about 7-10% idle and then when I opened the video it went to 60-70%. Odd. Please advise, thanks!

---

### Post by overdrank on 2009-01-21
> **ksheyman said:**
>  The video card is an ATI Radeon Xpress 200 (real piece of junk, but it worked fine with windows for video playback). 

Hi and I have had no luck helping with the xpress 200. :( The only thing that may help if it is a integrated graphics is to check bios and try and adjust the amount of memory shared.

---

### Post by Eddie Wilson on 2009-01-21
Hello. A question. Do you have Compiz running also? You may have to stop Compiz in order to get rid of the choppy video.

---

### Post by ksheyman on 2009-01-21
eddie,

what is that and how can i check if it is running?

---

### Post by Eddie Wilson on 2009-01-21
> **ksheyman said:**
> eddie,

what is that and how can i check if it is running?

This will tell you everything you need to know.

[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

Eddie

---

### Post by TVMA on 2009-01-21
ksheyman:

Click on 

System > Preferences > Appearance

Click on the "Visual Effects"  tab

what is it set? If anything other than "none"   select "none" apply, and try your video play back again.

Also, you can try:

type gstreamer-properties in terminal (Applications > Accessories in Ubuntu) and go to the video tab. Under Default Output, choose X Window System (no Xv).

---

