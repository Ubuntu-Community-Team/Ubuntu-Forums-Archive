---
title: "Uninstalling and reinstalling multimedia codecs"
date: 2009-06-02
forum: Multimedia Software
---

### Post by yonyz on 2009-06-02
Hi,

How can I uninstall all of the installed codecs?
I want to do a complete reinstallation, and I need to know what codecs exactly I should install and how to install them (preferably through the terminal).

The reason I want to do it is because of the awful video playback of VLC, Movie Player and Xine.
VLC does the best job of all three, but when I go fullscreen with it, I get a complete dark image and the audio is still working. The video works again after a few seconds or if I exit fullscreen. Sometimes my computer gets completely unresponsive and I have no choice but to reset it.
Is it possible that the problem is CompizFusion and not the codecs?

Thanks in advance.

---

### Post by xc3RnbFO8P on 2009-06-02
> Is it possible that the problem is CompizFusion and not the codecs?
Yes,
try in settings/preferences/compiz config settings manager under general tab, uncheck: Unredirect fullscreen

---

### Post by yonyz on 2009-06-02
It helps prevent system freezes, nothing else.
The video is played extremely slow and unsynchronized (the video is much slower than the audio) and it takes about 10 seconds for it to show picture - both problems occur only in fullscreen mode.

I think I still need to fix the codecs issue.
How do I go about completely uninstalling them all and then installing them?

VLC and SMPlayer are both having difficulty playing audio files, too.
VLC crashes very often and needs about 3 seconds to stabilize (before it stabilizes, the audio is choppy) and SMPlayer playes a 3 minutes song in 3 seconds (!).
Also, on Movie Player, there's sound coming out only from the right speaker, and it sounds horribly slow, as if it changes the audio sample rate.

---

### Post by xc3RnbFO8P on 2009-06-02
> VLC and SMPlayer are both having difficulty playing audio files, too.
VLC crashes very often and needs about 3 seconds to stabilize (before it stabilizes, the audio is choppy) and SMPlayer playes a 3 minutes song in 3 seconds (!).
Also, on Movie Player, there's sound coming out only from the right speaker, and it sounds horribly slow, as if it changes the audio sample rate.
Something like this:
[http://ubuntuforums.org/showthread.php?t=1146319]("http://ubuntuforums.org/showthread.php?t=1146319")

---

### Post by yonyz on 2009-06-02
Yup...

---

### Post by xc3RnbFO8P on 2009-06-02
What is your computer spec.?
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/124922]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/124922")
> i see the exact same problem, and i noticed that it seems to happen most often when i have a web page open in firefox that has some sort of flash video. i found that if i close totem and firefox, then restart totem to watch the video, the problem often goes away without a reboot.
> I have the same problem and found that I can run the following command...
sudo /sbin/alsa force-reload
This will remove and re-load all of the ALSA drivers. After doing this I have sound back AND video's play normally!
> I got slow playback with gstreamer until I changed some gstreamer options (this is a different problem, that others may have too).
$ gstreamer-properties
=> Video Output : autodetect

---

### Post by yonyz on 2009-06-03
My computer specs are as follows:

Intel C2Q Q6600
ATI Radeon HD2400XT (enough for Full HD playback on Windows)
Kingston 2GB DDR2 667Mhz
ESI Juli@ (audio card)

---

### Post by yonyz on 2009-06-05
My video and audio playback problems are all solved now. I've disabled visual effects.

---

