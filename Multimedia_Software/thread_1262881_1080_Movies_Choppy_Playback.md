---
title: "1080 Movies Choppy Playback"
date: 2009-09-10
forum: Multimedia Software
---

### Post by Fousheezy on 2009-09-10
Hey, I just read through [http://ubuntuforums.org/showthread.php?t=958893](http://ubuntuforums.org/showthread.php?t=958893)
That was about a year ago, so I was wondering if anything has changed. I can play 720p movie files perfectly with my system running a clean install of MythBuntu 9.04, however when I play 1080 movie files, the audio lags behind after a while and eventually the movie stutters and becomes completely choppy.

My system specs seem like they could be decent enough to handle 1080 but I'll leave that for y'all to assess. I have:
CPU: Pentium 4 3.0GHz cpu
RAM: 4GB of RAM
Video Card: I recently got a new video card: [MSI N94GT-MD512 GeForce 9400 GT 512MB 128-bit GDDR2 PCI Express x16]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814127412&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-") for which I got the recommended Ubuntu drivers.

Is there something I should try to alleviate the choppiness in 1080 playback? Is it fundamentally that my single core processor isn't enough? Should I consider getting an audio card to decode the HD audio in hardware and further take stress off the CPU or would that have such a minimal effect as to not matter?

Any help would be appreciated :)

---

### Post by tgalati4 on 2009-09-10
A second processor would help.  You could have a 6-GHz Pentium 4 and still have interrupt problems.

Boot a clean system, then examine /proc/interrupts

Run a 720p video for 5 minutes then examine /proc/interrupts

Run a 1080p video for 5 minuties then examine /proc/interrupts

The rest of your hardware is fine, you are just missing a processor.

Remember the Intel/Win XP media fiasco from a few years ago?  Same problem, single processors or Pentium D's (early dual core processors) don't have the bandwidth to handle 1080p adequately.

---

### Post by lykeion on 2009-09-10
Try mplayer with vdpau. I found it really helps when playing 1080 movies.

I think you need to compile mplayer yourself to enable vdpau. Search the forum and I'm sure you'll find a howto for this.

Wikipedia:
"VDPAU (Video Decode and Presentation API for Unix) is an API designed by NVIDIA for its GeForce 8 series and later GPU hardware"

"VDPAU API allows video programs to offload portions of the video decoding process and video post-processing to the GPU video-hardware."

---

### Post by Fousheezy on 2009-09-10
I'd prefer the offloading work with VDPAU over getting a new processor. I will check that out tonight.

If VDPAU doesn't work, is there something I should be looking for in interrupts? I'm guessing you think there will be a ton more interrupts when playing a 1080 than a 720?

If a dual core is the way I need to go, is there a dual core I can put on a mobo with a 478 socket? I google searched for something to that effect, and only came up with "mobile" processors- not entirely familiar with what that means. I'm assuming that if it says it's a intel duo 2 core processor and a 478 socket, it could still fit in a desktop motherboard even if it's a mobile processor? 

Thanks so much for the info so far.

---

### Post by Fousheezy on 2009-09-11
Using VDPAU fixed the problem! For those who come across this thread later, I did the quick and easy way of making mplayer use vdpau- added a repo which has an updated mplayer

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

Smplayer acts as a frontend for MPlayer and in the preferences menu just choose VDPAU as your output. If you then want mplayer to use vdpau even when not using smplayer, you can click around in the preferences until you find the actual command the gui is executing when displaying movies and copy that (editing options to make full screen default, etc)

---

### Post by lykeion on 2009-09-11
Great to hear this worked out for you, happy mplaying...

---

### Post by tgalati4 on 2009-09-13
Well, you found an extra processor.  It resides in your video card!

Interrupts will skyrocket when something gets overloaded:  the sound card can't keep up because the CPU is so busy processing video.  They show up as large interrupt numbers in /proc/interrupts.  Sometimes it's the southbridge trying to decode audio while streaming video.  If the ethernet is on the same chip, it gets toasty and starts spewing errors which also show up as NMI's--non maskable interrupts.

---

