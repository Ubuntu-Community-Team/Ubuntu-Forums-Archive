---
title: "smplayer sketchy, small bugs"
date: 2010-02-16
forum: Multimedia Software
---

### Post by helamsirrine on 2010-02-16
I am Running the latest version of smplayer from the distros, on a 64 bit Karmic system w/ nvidia 185 drivers for my gf9200(ish) on board card and compiz-fusion running. I love the gui, and mostly it works great for everything I want, but there are a few minor bugs that I can't seem to fix. 

Firstly the seek bar tends to get stuck(pauses playback) when I use the mouse scroll or drag the bar. I can usually unstick it and continue playback by clicking it again, but rarely I have to stop playback and press play again. This is not a big problem as I can usually resume playback, but it is an annoyance.

Also, smplayer has taken to executing 'move to workspace right' every time I open a file or even stop and start a playing file. This just started recently, and I can't think of anything i changed that could have caused this. I have no commands in the config file and, as I said, it just seems odd. 

Lastly is the screensaver issue. Namely that the screensaver still activates during playback even tho I have checked the 'disable screensaver' option. I realise this is a common problem, as I have attempted to fix it by editing the config file with a heartbeat command based on other threads. This seemed to work at first test, but the issue pesists. 

Any help in fixing these small annoyances would be greatly appreciated. smplayer is my favorite media player of all I've tried, If I could fix these bug's it would be perfect.
Thanks in advance.

---

### Post by rvm4000 on 2010-02-16
> **helamsirrine said:**
> Firstly the seek bar tends to get stuck(pauses playback) when I use the mouse scroll or drag the bar. I can usually unstick it and continue playback by clicking it again, but rarely I have to stop playback and press play again. This is not a big problem as I can usually resume playback, but it is an annoyance.

Change the audio driver from alsa to pulse in preferences -> general -> audio.

> **helamsirrine said:**
> 
Also, smplayer has taken to executing 'move to workspace right' every time I open a file or even stop and start a playing file. This just started recently, and I can't think of anything i changed that could have caused this. I have no commands in the config file and, as I said, it just seems odd. 

I don't know... Uncheck the option "Remember position and size" in preferences -> interface and see if that fixes the problem.

---

### Post by helamsirrine on 2010-02-17
Great! pulse audio fix woked. my seekbar works correctly. After turning off the 'remember' option the 'workspace right' issue persisted, however it seems to be fixed after a quit/restart of smplayer. Thank's buddy.

---

