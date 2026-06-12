---
title: "Royally screwed sound, and weird video shut-downs"
date: 2008-07-09
forum: Multimedia Software
---

### Post by PopeMatt on 2008-07-09
Okay, so I'm running Gutsy Gibbon and I read that pulseaudio lets you mute individual applications. Really cool. I followed a tutorial to install it on Gutsy, and the result was that only one application could have sound at a time. Really annoying.
I uninstalled all pulseaudio files and programs, reinstalled esound, followed a tutorial for setting that up... and I still have the same problem.
Also, this cool problem has started. I can play a video with VLC or Totem, but once it finishes, the program will automatically shut down. The same thing happens if I try to switch videos mid-play.
Help?

Thanks,
--Matt

---

### Post by xc3RnbFO8P on 2008-07-09
Did you try to start VLC or Totem from Terminal,
and see if there is some error message.

---

### Post by PopeMatt on 2008-07-09
This is what happens when I am already using sound in Totem, and try to play something in VLC. It plays, but no sound.

matt@Realize:~$ vlc
VLC media player 0.8.6c Janus

** (.:12211): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
[00000341] main private error: option glx-shm does not exist
*** PULSEAUDIO: Unable to connect: Connection refused
[00000337] oss audio output error: cannot open audio device (/dev/dsp)
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
[00000337] main audio output error: couldn't find a filter for the conversion
[00000337] main audio output error: couldn't create audio output pipeline

---

### Post by xc3RnbFO8P on 2008-07-09
I would make a fresh install,
here is Hardy Heron 8.04.1:
[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

---

### Post by PopeMatt on 2008-07-09
Uhm, well that's a nuclear option.
Besides Hardy doesn't play well with my ATI card. When I upgraded, huge problems were had. And I don't feel like a fresh install, that would mean a lot of program reinstalling and tons of fiddling to get Compiz working.
My sound worked fine until this week, there has to be a way to undestroy it.

---

### Post by xc3RnbFO8P on 2008-07-09
Sorry but I think there are to many errors to repair.
But I allway choose the easy way out.

---

### Post by PopeMatt on 2008-07-09
:'( I just want to have sound in two applications at once.

---

### Post by rainwalker on 2008-07-09
I don't think you're really going to make things worse (unless you lose sound completely) but you could try this guide for pulseaudio even though you're on Gutsy: [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by PopeMatt on 2008-07-10
I gave up, installed Hardy. It works better from a straight install than when I tried to upgrade. Blah blah.

---

### Post by xc3RnbFO8P on 2008-07-10
> It works better from a straight install than when I tried to upgrade.
:)

---

### Post by PopeMatt on 2008-07-10
I spoke to soon.
The problem isn't fixed.
I can have two videos playing at once with sound, but I still can't hear sound in flash in I have any other sound-using program in use.
It's not fair!

---

### Post by xc3RnbFO8P on 2008-07-10
Just read this first:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
and this:
[http://ubuntuforums.org/showthread.php?t=852822]("http://ubuntuforums.org/showthread.php?t=852822")

---

