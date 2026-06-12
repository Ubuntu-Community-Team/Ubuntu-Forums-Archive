---
title: "Audio performance in Feisty"
date: 2007-07-24
forum: Multimedia &amp; Video
---

### Post by brimlar on 2007-07-24
I just wanted to write here to see if others experience these problems (as in "are they to be expected") or if there were something I could change in my config to get the audio performance to improve.

DESCRIPTION OF PROBLEM:

I have a laptop, an HP nc8230 with 2GB of ram, a 1.8Ghx Core Duo processor, and an ATI x600 video card.  (1650x1080 resolution)  In short, no slouch of a laptop.  (Yes, I have the non-free driver installed)

However, I've noticed that with Feisty, certain acts in other applications can make Rhythmbox/Totem "hang" for a few seconds...the audio gets interrupted (silence), while I can only assume that it's because some other process started eating a large percentage of the CPU or RAM.  These acts include:

1)  Trying to scroll fast down the page in Firefox at Digg.com (the code there must be intense somehow?)
2)  Scrolling through any large document quickly
3)  With Compiz turned on, using the Ctrl-Alt-Down arrow "desktop preview" feature, or any graphical effect in a quick/intense manner
4)  Scrolling quickly through Rhythmbox

...you get the idea.  I discover a new one all the time.

Is this normal?  Is this being looked at for future releases (getting the audio to play 100% without interruption regardless of what other apps are doing)?  Or is my experience not the norm?

I'm just hoping someone has some advice -- thanks again for your time.

---

### Post by variona on 2007-07-24
looks like your graphic card and your very high resolution could be guilty - try a lower resolution, or a generic (i.e. non ATI) xserver

let's see :)

---

### Post by brimlar on 2007-07-25
Ok, I lowered my screen resolution and it's clear that video driver performance at those high levels is affecting performance of audio.

I just wish the audio wouldn't get interrupted...I hope we can reach a time where it will playback without interruption/pause despite what other processes are doing.  It kind of feels "not polished."

Sigh.  Thanks for the response, though.

---

