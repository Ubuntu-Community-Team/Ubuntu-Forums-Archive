---
title: "video freezes audio continues"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by anathema415 on 2008-03-16
Ubuntu 7.10 (Gutsy)
AMD Athlon 64X2 3800+
1 gig of ram
Nvidia 6150 SE (integrated)


Whenever I try to watch a video from my hard drive, or a DVD, using any player the video (actually, everything) will freeze for 10-15 seconds, but the audio continues to play, eventually the video unfreezes. When this happens I see processor 1 shoot up to 100% and processor 2 to about 95%. I ran vlc in debug mode and here is part of what I get:

> [00000335] a52 decoder debug: emulated sync word (no sync on following frame)
[00000340] main video output warning: late picture skipped (128941)
[00000340] main video output warning: late picture skipped (89078)
[00000340] main video output warning: late picture skipped (49096)
[00000340] main video output warning: late picture skipped (9110)
[00000336] main audio output debug: removing module "float32_mixer"
[00000336] main audio output debug: looking for audio mixer module: 3 candidates
[00000336] main audio output debug: using audio mixer module "float32_mixer"
[00000336] main audio output warning: resampling stopped after 16212073 usec (drift: -38752)
[00000336] main audio output debug: removing module "float32_mixer"
[00000336] main audio output debug: looking for audio mixer module: 3 candidates
[00000336] main audio output debug: using audio mixer module "float32_mixer"
[00000340] main video output warning: late picture skipped (3929)
[00000001] main private debug: removing all interfaces
[00000287] main interface debug: thread 3027143568 joined (interface/interface.c:258)


All the codecs I have installed I got from [here]("http://ubuntuforums.org/showthread.php?t=661833")

Any ideas?

---

### Post by chewearn on 2008-03-16
Which nvidia driver are you using?

---

### Post by anathema415 on 2008-03-16
169.12

---

### Post by chewearn on 2008-03-16
Take a look at the process list, see which process is consuming the 100% cpu?

---

### Post by anathema415 on 2008-03-16
Nothing. I think it only happens when everything freezes. By the time I get back to look, everything is normal again.

---

### Post by anathema415 on 2008-03-16
bump

---

### Post by anathema415 on 2008-03-16
I'm now fairly certain it's compiz.real.

When I run top it's taking up  62:37.79 of cpu time, which is more than anything else.

---

### Post by chewearn on 2008-03-16
Ok, this just a guess; check if you have xserver-xgl installed.  If yes, remove it.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/136650](https://bugs.launchpad.net/ubuntu/+source/xserver-xgl/+bug/136650)

---

### Post by anathema415 on 2008-03-16
No xserver-xgl installed. 

I was browsing around the compiz forums and someone was having a similar issue. Someone in there recommended turning off animations for compiz and so far that has worked very well. I'm watching a movie now with no freezes so far. I don't know if I'm quite ready to call this solved yet, but I think I'm getting there.

---

### Post by anathema415 on 2008-03-17
And the problem has started happening again](*,)

---

### Post by chensamurai on 2008-03-28
Hey, I have the same problem.
Video lags to a temporary stop while sound goes on. And then everything comes back to normal.

My computer:
Ubuntu 7.10 (Gutsy)
1 gb ram
Nvidia GeForece 6100

When I researched into this issue in the past, people have repeatedly said on forums to "install the proper driver" or something like that.

After checking my Nvidia driver, Ubuntu seams to only support the Nvidia GeForce 6 family, but not specifically one for a card such as GeForce 6100.

Could that be the issue to both mine and your problem?

---

### Post by anathema415 on 2008-03-28
That's a definite possibility. We have very similar specs, I have a 6150 card (integrated) and 1 gig of ram. What processor do you have?

---

### Post by chensamurai on 2008-03-29
My processor is "AMD Sempron 3400+" It's an old one. Not AMD 64, no where near.

OK so I completely fixed my problem. This is how I fixed it:
(also, my ubuntu system used to freeze for a couple of seconds randomly too. That was also fixed in this process)

First of all, i followed your idea of disabling the "Animations" in Compiz.
Video and other stuff still freezed. So I completely disabled all the luxury effects in Compiz and switched to the "None" graphical effects in the "Visual Effects" tab of the Appearance Preferences.

In that mode, all the shiny visual stuff is GONE. Everything else still works but with no cool, flashy transitions. Best of all, the videos from flash (such as youtube) and other sources (I'm watching some real media right now) all works perfectly.

Finally, when I switched up from the None effects to Normal effects (many graphical luxuries ,including Compiz effects, returned), the video was still working and my computer has no lag.

So that was my temporary fix. I don't know if it'll work for you though. try it!

---

### Post by anathema415 on 2008-03-29
Well I took your advice and set my machine to normal effects, hopefully it will work out for me too. If this works then it's just a matter of a new video card (integrated ones steal ram) and maybe more ram and I can have all my visual effects and non-freezing video too.

---

### Post by chensamurai on 2008-03-29
Yeah, I think the key to fixing this problem is to get more ram. 1 gig is not much nowadays eh.

Integrated video cards definitely takes up ram (my GeForce 6100 is integrated too).
By switching to low graphic modes such as Normal or None, a lot of system memory is saved.

Well I didn't fix my issue till I found this post by googling "ubuntu video freezes", so best of luck!

---

### Post by chewearn on 2008-03-29
I have two PCs with integrated nvidia graphics.

1. GeForce 6150; according to nvidia-settings, it takes up 512MB of 2GB in the integrated memory.  It did not have the problem reported here.  I have ubuntu with many compiz effects, plus dual separate screen.  Only minor annoyance is video playback have sporadic tearing on the larger resolution screen (1680x1080).

2. GeForce 6100; this one reported by nvidia-settings to be using 256MB out of 1.5GB.  Previously, I test Kubuntu on it, tried installing compiz.  The xorg cpu load tends to shoot to the roof periodically, so after that I removed compiz.  But I don't really like KDE; now I ran Xubuntu on this PC, with no compiz installed.

So, I agree with your analysis about problem here could be due to lack of memory, or possible lower bandwidth of the shared memory..

---

### Post by anathema415 on 2008-03-29
Mine is using 512MB of my 1 gig so I think we know the culprit now.

---

### Post by anathema415 on 2008-04-04
After nearly a week of no problems it's started again.

---

