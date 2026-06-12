---
title: "Karmic sound - flash vs applications problem"
date: 2010-02-25
forum: Multimedia Software
---

### Post by bgc on 2010-02-25
Hi, since I upgraded to Karmic I have no end of issues with sound. I mainly use mpd, the occasional youtube video, lastfm client, and maybe vlc. Since the beginning, by following some how-tos, I got sound to work generally. However, at each reboot it would stop working. That is to say, no sound in flash videos, and mpd jamming. With some tinkering (not sure what it was that did the trick) it would then work again. But each reboot would mean the same time wasted and random meandering to get things to work. I have tried reading up on the issue, and have tried following several troubleshooters. Now it seems I can either play sound on mpd, or on flash videos, but not both. I am completely at a loss here, and would really appreciate some help!

I know there are countless posts on sound issues, but none solved the problem for me.

Thanks for any help you can give me!

bgc

---

### Post by mörgæs on 2010-02-25
Then you have probably also tried
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

9.10 will probably be the only Ubuntu since 5.10 I am not going to install. You could try 9.04 or 10.04:

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) (in alpha, but pretty stable)

---

### Post by bgc on 2010-02-26
Yep, it includes that link too! I have no idea, all the troubleshooting shows that things should be fine, but they're clearly not, and I really can't go through a fresh install right now. I guess my only option is to wait for the next one, and *hope* that this stops being an issue!

---

### Post by mörgæs on 2010-02-26
I meant, you could just try booting with a live CD to get a feeling of how another version works your hardware. After that you can decide whether or not to install.

---

### Post by mörgæs on 2010-03-02
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by bgc on 2010-03-02
Compiling the latest stable ALSA version didn't do it for me. What I think made things a bit better (but not everything works yet) is adding the Ubuntu Audio Dev team PPA:

[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

I even get the impression that what doesn't work (MPD) is because of an error on my side in the configuration file.

---

