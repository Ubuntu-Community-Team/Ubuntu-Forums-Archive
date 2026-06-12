---
title: "Encoding video formats"
date: 2010-05-20
forum: Multimedia Software
---

### Post by David Deu on 2010-05-20
Hi,
I've installed the ffmpeg to encode video files, but when I'm starting to convert, it says "Unknown encoder libmp3lame", what does that mean? that I have some encoder missing? because I checked in the Software center for "libmp3lame" and I found it already installed.

Thanks,
David

---

### Post by andrew.46 on 2010-05-20
Hi David,

You are probably missing a few encoders. Have a look at this page for some solutions:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

### Post by David Deu on 2010-05-20
Thank you very much!
I succeed to encode Through the textual way, but then I installed the Winff which meant to be the graphical way for ffmpeg, and when I've started to convert he wrote "ffplay not found", what's that?
Thanks'
David

---

### Post by wishingstar on 2010-05-20
Hi,

I use video conversion extensively, and the one big beast that can do it all for me is [Handbrake]("http://handbrake.fr/?article=download").

also, to get support for all formats you can run:
```
sudo apt-get install ubuntu-restricted-extras non-free-codecs w32codecs
```

Hope this helps!

WishingStar

---

### Post by David Deu on 2010-05-20
> **wishingstar said:**
> Hi,

I use video conversion extensively, and the one big beast that can do it all for me is [Handbrake]("http://handbrake.fr/?article=download").

WishingStar

Unfortunately, with HandBrake I couldn't convert. (I've tried from .avi to .mp4) I don't even get the option to add to queue.

---

### Post by wishingstar on 2010-05-20
that's odd, handbrake was the only one that worked for me, maybe it's a codec issue then, or perhaps handbrake has some dependencies (not likely but still).

---

### Post by FakeOutdoorsman on 2010-05-20
> **David Deu said:**
> Thank you very much!
I succeed to encode Through the textual way, but then I installed the Winff which meant to be the graphical way for ffmpeg, and when I've started to convert he wrote "ffplay not found", what's that?
Thanks'
David

Did you compile FFmpeg?  If yes, then perhaps you will need to manually tell WinFF where *ffplay* is located.  I'm not sure what version of Ubuntu you are using, but this bug might be what you are experiencing:

[WinFF - Issue 56: Add /usr/local/bin for FFplay executable search](http://code.google.com/p/winff/issues/detail?id=56&can=1)

---

### Post by JohnAStebbins on 2010-05-20
> **David Deu said:**
> Unfortunately, with HandBrake I couldn't convert. (I've tried from .avi to .mp4) I don't even get the option to add to queue.
Let me guess.  You're running lucid and tried to run the 0.9.4 release of handbrake.  Lucid broke that release.  You have to use the snapshots.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by wishingstar on 2010-05-20
JohnAStebbins,

I just tried handbrake and you're right, I haven't used it in a while but the snapshots worked like a charm :) thanks!

---

### Post by David Deu on 2010-05-20
> **JohnAStebbins said:**
> Let me guess.  You're running lucid and tried to run the 0.9.4 release of handbrake.  Lucid broke that release.  You have to use the snapshots.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots]("https://edge.launchpad.net/%7Estebbins/+archive/handbrake-snapshots")

Right! And the snapshots solved it.
Thank you,
David

---

