---
title: "No sound in Flash in Xubuntu 12.10."
date: 2013-03-06
forum: Multimedia Software
---

### Post by milesianmedia on 2013-03-06
Hi, everyone. I've been trying to fix this myself, but I can't seem to find very much info online, so I came here. I don't seem to see anyone else with this problem, but if there is, it would be nice if you could point me to it. This is my first post on this forum, so if it's in the wrong place or something please forgive me.
Anyway.
Recently I attempted to compile ffmpeg from scratch, using instructions I found [here]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide"). It didn't work for my purposes, but that is okay. However, in installing some of its dependencies, I fear I may have somehow messed up my sound system (by inadvertently downgrading some packages, perhaps). After much troubleshooting, I was able to get PulseAudio to show up again in the "sound card" dropdown of the xfce sound mixer, and I can play sounds from other applications such as Rhythmbox. I can also hear sounds from audio and video tags in Firefox. When I am playing a sound from these, an entry appears in pavucontrol called "ALSA plugin [firefox]: ALSA playback." However, when I try to watch a video on YouTube, it appears to start (with no sound), then jumps back to the beginning, then plays from the beginning with still no sound. This doesn't happen with any other flash content, but it is strange. I know this is kind of a vague problem, but I'm not really sure what other information to provide. I am willing to provide any information you desire.

---

### Post by carl4926 on 2013-03-06
ffmpeg is in the repos
why mess and Jeff up your system

what browser?
Have you tried installing Google Chrome?

---

### Post by milesianmedia on 2013-03-06
I was looking for a way to record my screen and also application sounds, which I had found that the repo version of ffmpeg didn't do? (the compiled version didn't seem to do that either, but ...) 
I was originally trying it with Firefox, but I also tried Chromium and Midori, both of which had the same problem.

---

### Post by carl4926 on 2013-03-06
No youtube issues here in xubuntu, whatever browser....
Try rebooting

---

### Post by milesianmedia on 2013-03-06
Just realized I should clarify: The "this doesn't happen with other flash things" only applies to the skipping back to the beginning. There's no sound in any flash content.

---

### Post by carl4926 on 2013-03-06
> **milesianmedia said:**
> Just realized I should clarify: The "this doesn't happen with other flash things" only applies to the skipping back to the beginning. There's no sound in any flash content.

Still all good here

---

