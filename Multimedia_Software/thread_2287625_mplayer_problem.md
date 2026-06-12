---
title: "mplayer problem"
date: 2015-07-21
forum: Multimedia Software
---

### Post by Evil Wayz on 2015-07-21
I have a file encoded in on2 vp7.  Nothing will play it but mplayer from command line.  I thought SMPlayer was a mplayer frontend gui, but when I play the file thru smplayer all I get is sound.   don't see anywhere in the preferences a place to tweak it  What am I missing?   I'd rather not convert six seasons of a show to xvid.

---

### Post by sudodus on 2015-07-21
It is a lot of detailed work to make GUI shells, so they are seldom complete, and some unusual tasks and options might work only from the command line. I often run mplayer from the command line, and it is good enough for me, so I would not convert the video clips. I suggest that you give it a chance. When you learn several of all the things you can do via the command line, you might even prefer running mplayer that way :-)

The manual ```
man mplayer
``` is long and might be scary the first time you read it, but after a while you get used to it and learn how to find what you want. You can probably also find good tutorials via the internet.

*Edit:* Or ask for a specific task or option here at the Ubuntu Forums :-)

---

### Post by Evil Wayz on 2015-07-21
Basically what I want is for smplayer to look for and use VP07.  Or I guess it would be vp7vfw.dll  since I'm using mplayer.

---

### Post by ron998 on 2015-07-21
> **Evil Wayz said:**
> ...Basically what I want is for smplayer to look for and use VP07...
Hi
Make sure you're using the latest version of SMPlayer from the PPA here ---> [https://launchpad.net/~rvm/+archive/ubuntu/smplayer](https://launchpad.net/~rvm/+archive/ubuntu/smplayer)
If it still doesn't work, submit a "Feature Request" ticket here ---> [http://sourceforge.net/projects/smplayer/](http://sourceforge.net/projects/smplayer/)

---

### Post by sudodus on 2015-07-21
We, the people at the Ubuntu Forums, are only users of smplayer. But you are welcome to ask the developers of smplayer to make this improvement. The standard way of doing it is to file a bug report against smplayer at Launchpad.

Edit: ron998's direct method might work better :-)

---

### Post by papibe on 2015-07-21
Hi Evil Wayz.

These information may be useful:

These days 'smplayer' is using mplayer2 instead of vanilla mplayer:
```
$ apt-cache depends smplayer | grep mplayer2
    mplayer2

```
Which install a binary called just 'mplayer':
```
$ dpkg -L mplayer2 | grep bin/mplayer
/usr/bin/mplayer
```
Make sure you are using the same underneath player for SMplayer. Go to:
```
Options -> Preferences -> General -> Mplayer/MPV executable
```
I believe installing vanilla mplayer would uninstall mplayer2, so can 'swap' them to check which one works better.

I also understand that mplyer2 is fading in favor of 'mpv', which now is recommended as the underneath player for SMplayer (read [this]("http://askubuntu.com/questions/644398/how-do-i-deal-with-mplayer2-forwarding-latency")).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sudodus on 2015-07-21
@ papibe: Thanks for the tip about ***mpv*** :-)

Have you used it? Is is using (almost) the same options and parameters?

---

### Post by papibe on 2015-07-21
I haven't play much with the options, however I can say that:
[LIST]
[*]It works transparently if you use it in SMplayer
[*]If you install it from: ppa:mc3man/trusty-media it supports VP7 both from mpv and SMplayer.
[*]You can keep mplayer/mplayer2 since it does not conflict with it.
[/LIST]
So far, I would recommend it.
Regards.

P.S.:  ppa:mc3man/trusty-media is also the recommended ppa for the latest FFmpeg (static builds).

---

### Post by sudodus on 2015-07-21
Thanks again - this is valuable information :-)

---

### Post by Evil Wayz on 2015-07-22
Because I'm lazy I tried Papibe's instructions first, as soon as I added the ppa and updated, i got fresh versions of ffmpeg and smplayer.  I installed mpv, and under options>preferences>General>MPlayer/MPV executable I changed the command from mplayer to mpv.  Works like A charm.  THanks peeps, I got six seasons of CHiPs to watch now so I'll be seein' y'all.  And thanks to all y'all, I was fighting with it late into the night.

---

