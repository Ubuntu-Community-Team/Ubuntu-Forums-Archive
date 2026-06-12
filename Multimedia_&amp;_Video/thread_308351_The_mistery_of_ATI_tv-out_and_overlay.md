---
title: "The mistery of ATI tv-out and overlay"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by cristianrosa on 2006-11-27
I have a great confusion about the many ways avaiable to get tvout with ATI.
First doubt:
The most common way of getting tv-out with fglrx is setting the options "DesktopSetup" "clone" or dual head in xorg.conf.
With these options you get on the TV a downscaled version of the signal from the monitor.
AFAIK, if you watch a movie in fullscreen, then you get a downscaled version of the movie on the TV, and this has lower quality than the output of hardware dvd player. Is this correct?
Second doubt:
I heard about an option from the ati control panel in windows called "overlay theater mode". When it is enabled on a radeon card the normal desktop clone will be displayed on the tv until a video overlay is detected (meaning a software player is playing a video using the video cards hardware acceleration ie. overlay). Then the tv display is automatically switched to displaying that video full screen w/ overscan (no black borders) and at *EXCELLENT* quality. As far as i understand if you minimize stop or close the player the overlay goes away and the tv goes back to displaying a clone of the desktop.
Is it possible to get the same functionality using flgrx?
Is this equivalent to configure fglrx in dual head, and then setting the tv screen to 720x480 (NTSC-M standard res) + overscan?
If anyone has any clues about these issues, i would very glad to hear them :D
Thanks in advance :cool:

---

### Post by jkwarras on 2006-11-28
AFAIK the theater mode doesn't exist in linux. If you use 800x600 or 1024x768 as your desktop resolution you could use clone mode. Anything else (or if you'll like to have an independent screen) you could use a dual setup (that's what I use). This way you could start applications in the second screen (TV) while leaving first screen 'untouched'.

---

### Post by cristianrosa on 2006-11-28
> **jkwarras said:**
> AFAIK the theater mode doesn't exist in linux. This is a bad news :( 
> **jkwarras said:**
> 
If you use 800x600 or 1024x768 as your desktop resolution you could use clone mode. Anything else (or if you'll like to have an independent screen) you could use a dual setup (that's what I use). This way you could start applications in the second screen (TV) while leaving first screen 'untouched'.Using the dual-head approach, is it possible to configure the tv screen to use 720x480 so it does not need to be downscaled?
Can ATI's boards handle that resolutions?

Have you ever heard about the "texturedvideo" option of fglrx?
Does it has better quality than XV?

Thankyou for your help!

---

### Post by jkwarras on 2006-12-07
> **cristianrosa said:**
> This is a bad news :( 
Using the dual-head approach, is it possible to configure the tv screen to use 720x480 so it does not need to be downscaled?
Can ATI's boards handle that resolutions?
You could try to setup this as resolution in the xorg.conf, and see if it works for you.

> **cristianrosa said:**
> Have you ever heard about the "texturedvideo" option of fglrx?
Does it has better quality than XV?
I've just tried and it reboot my gdm. I don't know what it does.

---

