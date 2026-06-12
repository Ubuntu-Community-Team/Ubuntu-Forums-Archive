---
title: "Pulseaudio Distortion"
date: 2011-09-06
forum: Multimedia Software
---

### Post by osarusan on 2011-09-06
I'm operating on a fresh 11.04 install, x64 Ubuntu.

I've had this problem for a long time now, probably back since 10.04, but under 11.04 it happens much much more often, nd its getting very frustrating.

Occasionally, seemingly at random, but usually when I am using a lot of memory like playing a game or watching a hi-def video, pulseaudio goes crazy and distorts. The sound crackles and sounds "roboty" and it never recovers. I have to restart pulseaudio to fix it. After that it works fine for a while, but eventually it always happens again.

I've searched the forums and the pulseaudio solutions thread but I can't find any clues. Is there anyone who knows about this distortion problem who can help me?

---

### Post by Pilot_51 on 2011-09-14
I believe I have the exact same issue, also for awhile, though not sure if it's worse in 11.04. It is happening once or twice a day on average.

Pulseaudio works fine for awhile and then suddenly becomes distorted, or I return to find it distorted usually overnight. One possible trigger I noticed seems to be when memory gets full around the point where swap starts being used. I also noticed that it can be triggered by sounds, such as TTS (Mumble) or an IM message while I'm playing a game.

I would like to see this solved or at least a better reset than I'm using now such as command line so I can script it. I used to restart Pulseaudio, but that caused problems with nearly all running programs needing restarted for audio to work again. A better way I found to reset it is in Sound Preferences, Hardware tab, select the device and change the profile to Off and then back where it was (Analog Stereo Output in my case). This has very few problems with running applications, they will continue playing audio undistorted.

I'll edit or post again if I find a way to reset it in command line, or better yet, an actual fix.

Motherboard: Foxconn C51XEM2AA
Audio device (output only): Realtek ALC882D HDA (integrated)

EDIT:
Got the commands/script!
Here's what I'm using. It will most likely be different for you.
```
#!/bin/bash
pacmd set-card-profile 2 off
pacmd set-card-profile 2 output:analog-stereo
```
The "2" is the card index, which can be found with "pacmd list-cards".
The "output:analog-stereo" is of course the profile, which I found using "gnome-volume-control --debug" and looking at the "Profile" lines.
You'll probably want to test it while Sound Preferences > Hardware is up with the profile manually set to Off so you see right away if it works.

---

### Post by osarusan on 2011-09-14
Yes, that sounds exactly like the problem I have.

Your workaround is better than mine! I wish they would fix this though... it's been happening for a long time and you'd think someone would have done something by now...

I'll try your workaround solution. It'll be easy enough to make a shortcut on my panel to run that script. Thanks for that tip!

---

### Post by freakycheeseman on 2012-07-25
Hey, having the same problem- script works for me too, except I'm less certain about hard-coding it, as the index value changes based off of what microphone/etc I have plugged in.

Has there been any word on a more permanent solution?

---

