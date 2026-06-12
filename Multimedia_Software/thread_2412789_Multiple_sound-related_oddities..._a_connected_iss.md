---
title: "Multiple sound-related oddities... a connected issue?"
date: 2019-02-17
forum: Multimedia Software
---

### Post by dnbattley on 2019-02-17
Dear Forums,

I hope you can help: I am a slightly-but-not-very experienced Linux user who has dabbled with a number of distros over the years, but I am stumped by a number of odd issues arising in my current build, all apparently related to my sound setup.

As background I am running Ubuntu 16.04, on an AMD Ryzen rig which I built, and the specific issue that has prompted this relates to getting Openshot to play sound - when I import an MP3 file (or even a WAV, if I convert using ffmpeg) it crashes if I make any attempt to play it back, requiring me to kill the openshot-qt process. Normally I would presume to take my issue to the Openshot forums, and indeed some others have had similar-sounding problems in earlier builds, but these are marked as fixed in my current version (2.4.3). HOWEVER, this is not the only time I have found sound... oddities, and I suspect a deeper root cause that I hope the wisdom of this forum can help me discover.

My suspicions are aroused because of some other sound issues I also have:
i) an occasional crash on the game "Battletech" that seems to arise when an opening cinematic is played (the video plays, but intermittently the sound does not, in which case then the computer becomes less and less responsive - including for mouse movement - until it eventually throws me back to the desktop). Sometimes this is fixed by immediately re-running the game (whereafter no issues occur), and I have found - by chance - that running alsamixer and manually setting the output in the terminal screen from the NVidia graphics card over to the Generic output seem, bizarrely, to avoid the issue. 
ii) I am unable to capture any sound using "vokoscreen" screen capture - it records video fine, but refuses to record if I include any sound channel.

Otherwise sound works as expected: videos and audio files and websites play as expected. The lack of consistency makes this challenging to understand, but I hope someone can help me to unravel the mystery, before I get to the point where I have to re-install.

I have found from my internet searching on this topic that audio settings are... complicated. I have previously tried to make adjustments to pulseaudio and alsa settings, but quickly get out of my depth (arguably having never been in my depth).

Hoping you can help,

---

