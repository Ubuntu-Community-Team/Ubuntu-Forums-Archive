---
title: "[SOLVED] MythTV old hardware and capture card, video sync problem"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by UncleJock on 2007-11-30
Hello, all!

New to linux. Always willing to learn/research answers. Getting frustrated with this project.

I've attempted to build a MythTV PVR box out of older hardware.
It's having a severe video/audio sync issue with the video being around 8 seconds behind, but clear. Audio is also good. If the audio sync setting is adjusted to compensate, as it nears sync, it starts dropping most frames, until I adjust it back.
Also sometimes buggers video everywhere else, including the frontend, AND the desktop, until I restart the system.
The audio is currently wire fed directly from the cap card into a channel on the sound. Am I right in thinking this might have something to do with audio coming through "early"? If it's because it needs to be read from the hard drive in sync with video, then I'll have to research how to play with the audio. 

I'm willing to go buy a Hauppauge 350, if the general opinion is that it'll solve this sync issue, however I'm not willing to buy a new system for this project. I'm a firm believer in recycling hardware into useful projects... and I'm strapped for cash.

Ubuntu 7.10, current updates. Xserver, etc etc.
Intel P4 1.7GHz
512M RAM
ATI 9200 AGP 8x (4x in this box) video card (recognized, no restricted drivers)
ATI TV Wonder capture card (recognized, no restricted drivers)
IDE hard drives

I'll post more info on request... because I'm not sure yet where to find it. :)

---

### Post by UncleJock on 2007-12-01
OK.
I found my solution to the sound sync issue.
The sound was wired from the capture card through an audio channel, and the separate channel digital audio from the capture card was not the default for the TV.
The trouble was that I hadn't realized that the video/audio are dumped to drive, then read back to display. It was keeping things in sync just fine, but I was hearing audio direct instead of what it had recorded. The weird frame drops as it approached sync, were because it was trying to read/display within milliseconds of writing to the drive.

I switched on the BT878 as the capture audio. Bingo.
The sound then was in sync, along with a pre-echo of the audio. OK. Weird, but closer.
Was stumped for all of a few seconds, until I reached into the guts and pulled out the audio patch wire from the capture card. Tada! The pre-echo dissapeared.

So this old box is working fine now, and I'm happily tweaking things. Wondering if another antique capture card would work for another channel. Probably not for recording, but watching.

---

