---
title: "[Solution] Logitech G15 (v1 with 18 G keys) Multimedia Key function and Volume Cntrl"
date: 2008-12-03
forum: Multimedia Software
---

### Post by zeifertstc on 2008-12-03
Believe it or not, setting up the sound was the easiest thing I've had to do. I'm not sure if you're using Ubuntu 8.04 or 8.10. Right now, I'm waiting on my media for 8.10 to arrive by mail. In the mean-time I'm on 8.04. My solution for surround and master volume control by multimedia keyboard (in conjunction with Audacious) is real simple. 

First, make sure your Sound Blaster Audigy is fired up. By default, the additional audio channels you need are nearly if not totally muted (turned all the way down. Alsamixer will help you set your audio better as you can see all levels at once (enter "alsamixer" into a terminal to run it). Once you have your volume levels where you want (all of them even for best results). It may be necessary to create a file in your home folder (.asoundrc) and enter the following into it:

```
pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
} 
```
> The above code is for a 5.1 Surround Sound Speaker setup. After making this file it may be necessary to Ctrl+Alt+Backspace or restart your system so it will be loaded.

To make sure your speakers are producing sound you can run a speaker-test like so: 

> For 4.0 surround (two speakers in front, two in the back):

speaker-test -Dplug:surround40 -c4 -l1 -twav

For 5.1:

speaker-test -Dplug:surround51 -c6 -l1 -twav

For 7.1:

speaker-test -Dplug:surround71 -c8 -l1 -twav



If the nice lady tells you the names of the speaker she's speaking from and it actually sounds like that speaker is working, we'll proceed to making your keyboard's volume control "master" all these channels that are now working.

Go to System -> Preferences -> Sound -> Devices (which should be already open by default)

Under default mixer tracks you should see a drop menu with your sound devices listed, make sure yours is selected (CA0106 for me and my Sound Blaster Audigy 24-bit) If all is good there, then you should see a scroll box under that drop menu with different channels listed. Might look like:

Line in
Microphone
Phone

If you scroll down far enough you will find:

Analog Center/LFE
Analog front
Analog rear

These three should be all you need, but if you want you can include Analog Side (especially if you have a 7.1 speaker setup, mine is 5.1 so Side might not be needed)

Press and hold Ctrl and click on those three or four channels to highlight them. After that, click close and test your multimedia keyboard volume control, it should raise and lower the volume for all channels at once. 

If you're like me and using Audacious, your multimedia keys are simply activated by going into Audacious preferences, clicking the "General" tab and locating "Gnome Shortcuts", check the box there and close the window. Your multimedia keys should now function correctly. For those running 8.10, if this doesn't seem to work, try toggling your num lock and try the keys again. If this still doesn't work, then you may wish to seek out xmodmap and use it in conjunction with xev (a command you enter in the terminal) to find out your multimedia keycodes and entering this info to xmodmap to get your keys working for you. I'm no expert with xmodmap but I have seen it work for others.

(NOTE: This has only been tested with a Logitech G15 V1 keyboard with the 18 G keys)

---

