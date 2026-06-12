---
title: "Still have sound issues on jaunty with flash + pulseaudio"
date: 2009-10-25
forum: Multimedia Software
---

### Post by Lucky75 on 2009-10-25
Hi all,

I'm still having annoying sound issues on Jaunty. I'm using pulseaudio and the simultaneous stream. 

When I open pauvcontrol while playing a movie, say in VLC, it shows up fine. I can even play multiple movies and get sound at the same time.

The problem comes from flash in firefox, where if I start streaming a flash video or something, and then attempt to watch a video in VLC (or others), the VLC sound doesn't work, although it does show in pauvcontrol. The flash audio does NOT appear.  This is particularly a problem when I'm say trying to watch a video and playing a flash game or something with sound that I don't particularly care about, but to be able to watch a video I have to close down firefox first, open the video, and then re-open firefox. 

If I start a movie first and then start a flash stream, the sound in flash does not work.

I also have an issue whereby if I open VLC (or others) first and then open a flash video in firefox and then close down vlc, the sound goes all buggy and repeats the same beeping/clicking sound until I "kill -9" firefox.

I would guess that firefox just isn't using pulseaudio? How do I get it to do that? Any other suggestions? I would prefer to use pulse instead of ALSA I think.

I've read a bunch of those "comprehensive sound guides" to no avail, so I would appreciate direct instructions if you have an idea what's wrong.

Thanks a lot!

---

### Post by Lucky75 on 2009-10-26
up

---

### Post by HappyFeet on 2009-10-26
Try:
```
sudo apt-get install libflashsupport
```
Then restart firefox.

---

### Post by RichardLinx on 2009-10-26
If Happy Feet's suggestion doesn't work, you can just remove pulse audio and install esound. See here: [http://ubuntuforums.org/showpost.php?p=8139087&postcount=2](http://ubuntuforums.org/showpost.php?p=8139087&postcount=2)

---

### Post by Lucky75 on 2009-10-27
I've read a few guides that say libflashsupport is a BAD thing to install on one's system, and that it's possible to get flash to work without it. Any suggestions?

> 
Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

[http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic](http://ubuntuforums.org/showthread.php?t=789578&highlight=usb+mic)

Not too sure what esound is yet, or if it's better than pulse. Does surround sound 5.1 work on it? Would it be recommended over pulse?

---

### Post by markbuntu on 2009-10-28
You should try this:

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

VLC uses the xine engine for sound. You need to set xine to use pulseaudio if you want to prevent a conflict. If you are using Jaunty you need to install ui-xine to get to the controls.

---

### Post by Lucky75 on 2009-10-29
VLC is set to use pulse, that's not the problem ;)

---

### Post by Lucky75 on 2009-11-01
up

---

### Post by Lucky75 on 2009-11-02
bump?

---

### Post by Lucky75 on 2009-11-04
up

---

### Post by sleepee on 2010-03-01
i know this is a very old thread, but i found a fix that worked for me...
just in case the OP or anybody else is looking for a solution to this problem

check out my thread:
[http://ubuntuforums.org/showthread.php?t=1412153](http://ubuntuforums.org/showthread.php?t=1412153)

---

### Post by Lucky75 on 2010-03-03
Yeah, I just upgraded to karmic, and then used the 2.6.32 kernel. Works great now *knock wood*

---

