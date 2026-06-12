---
title: "DVD Styler Crashes When Trying to Create and ISO"
date: 2015-05-01
forum: Multimedia Software
---

### Post by uRock on 2015-05-01
Every time I try to start a project in DVD Styler it crashes and I get this error listing in syslog. ```
kernel: [ 1417.676687] traps: dvdstyler[5860] trap divide error ip:7f561f2e3d2c sp:7fffa78e0b60 error:0 in libavformat.so.54.20.4[7f561f264000+10e000]
```At first I thought it was crashing because the file was on an external drive, so I copied to the local disk. It still failed, so I tried using a video with a smaller file size, which didn't work either. 

Any ideas on how to troubleshoot and fix this issue?

Ubuntu 14.04 AMD 64

Cheers & Beers,
uRock

---

### Post by speartip on 2015-05-02
I can't help you, other than to say that I have always had that problem with dvdstyler.
After much searching and no answers I went back to using devede.

---

### Post by uRock on 2015-05-03
Devede is just ignoring me when I hit the button to create an image. DVD Styler had been working great for me up until recently.

---

### Post by mc4man on 2015-05-03
I'd say dvdstyler is a real mess. Your error is in some lp bugs, just not as seen in syslog 
(ck. /var/crash/ for the crash > d click on > details, probably something like - 
av_interleaved_write_frame()

It gets worse in dvdstyler 2.7+, then it tries to create a menu the size of a dvd [https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1391803](https://bugs.launchpad.net/ubuntu/+source/dvdstyler/+bug/1391803)

Really not solved until version 2.9.x which isn't in Ubuntu & requires newer wxsvg than in 14.04 [(here]("https://launchpad.net/~mc3man/+archive/ubuntu/testing6") but requires careful read.

The wierd thing about 2.9.x is that it does actually work ok but - 
A vlc built off of ffmpeg shows a basically blank menu though you can click on an active area to start playback or open 2nd menu.  The error in vlc is " [mpeg2video @ 0x7fc8a8173400] warning: first frame is no keyframe" see scr 1

Apparently libav ignores & shows menu.. scr. 2

Though if clicking bottom button in vlc (ffmpeg) then the 2nd menu works scr. 3

(this just indicates slightly improper menu creation or some vlc w/ffmpeg flaw.. probably the later.
Haven't tried the test disk yet in a hardware dvd player

---

### Post by speartip on 2015-05-04
> **uRock said:**
> Devede is just ignoring me when I hit the button to create an image.
When you say "ignoring" do you mean it literally does nothing, or does the program crash?
The reason i'm asking is because there is a bug in Devede causing it to crash when you change the output folder, but i've never heard of it doing nothing before.

---

