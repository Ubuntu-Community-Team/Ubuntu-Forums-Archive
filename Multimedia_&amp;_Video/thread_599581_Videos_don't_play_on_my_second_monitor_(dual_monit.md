---
title: "Videos don't play on my second monitor (dual monitors)"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by watermark on 2007-11-01
I'm using gibbon and I have a dual monitor setup.  When I'm playing a video in any media player, videos only work on my left monitor.  When I drag the window to the right monitor, the video will either turn green or freeze at the last frame it was on (depending on the codec used I think.)

I'm using the nvidia drivers from the restricted driver manager and I used the "screens and graphics" tool to setup the dual monitors (which that tool is far from perfect).   I'm on a hunch saying it's the xorg config that this tool created that is causing this.

Any ideas?

---

### Post by Light- on 2007-11-02
I dont trust that tool either, it screws with your xorg.conf badly

Does the nvidia control panel have an option for setting up dual monitors via TwinView? If so, I would use that instead and see what happens (be sure to start off with a fresh xorg.conf)

---

### Post by sloggerkhan on 2007-11-02
This might be related to your card abilities. I have a ati x700. Max texture size for the card is 2048x2048. So for some apps I need to move the overlay to the 2nd monitor to get video to work on it. Might be something similar.

---

### Post by Light- on 2007-11-02
Hmm? I have two monitors, one 1680x1050 and one 1024x768, and the max texture size of my card is 2048x2048, so the monitors obviously exceed this, however playing video on both monitors works fine with ati's big-desktop

---

### Post by sloggerkhan on 2007-11-02
I should clarify. If I am only running one video in an app it can be on either monitor and it does depend on the type of video overlay I'm using. For example, VLC will only fullscreen to one monitor. Xine will full screen to either. As noted previously, it depends on if you are using xv overlay or what. There can be mysterious interactions in how this behaves, also. I will try to document how it behaves and explain more fully.

---

### Post by watermark on 2007-11-04
It's not a limitation of the card...it worked fine in feisty.  The only change in gutsy from feisty in this area iis the screen and graphics tool and the version of xorg (I believe).

It's kinda looking like I'm gonna have to manually redo my xorg.conf.  I was really trying to avoid this.  I'm no super newb, but I'm no xorg master either.  The screen and graphics tool really isn't ready for production machines.  It's badly needed, but it's not ready yet.

Anyone know of a quick fix to this problem?

---

### Post by matthewcraig on 2007-11-12
> **watermark said:**
> I'm using gibbon and I have a dual monitor setup.  When I'm playing a video in any media player, videos only work on my left monitor.  When I drag the window to the right monitor, the video will either turn green or freeze at the last frame it was on (depending on the codec used I think.)

I have the same problem.
[https://answers.launchpad.net/ubuntu/+question/16206](https://answers.launchpad.net/ubuntu/+question/16206)

---

### Post by watermark on 2007-11-12
I also realized that restarting X seems to fix the problem...which leads me to believe it's a problem with X or the xorg.conf setup.  (I think the Nvidia module is loaded at startup and not at X restart?)

My problem seems to be changing though.  Sometimes it does what I've described above, and other times I have to restart X between every video.  I play a video, close the video player, then try to open another video and the 2nd video doesn't play.  If I leave the video player open and play the 2nd video, it works fine.

It seems to be for every type of file with any player I use (tried totem w/ xine, vlc, and mplayer).  Even flash videos do it every once in a while (although not as often, don't understand this either).

Like I said above, I really think that configuring X manually will solve the problem, I just haven't put the effort into it to find out yet.

---

### Post by matthewcraig on 2007-11-13
Read through my link.  I've been working around this problem for a while...

While videos will consistently fail on one monitor, they will consistently play correctly on the other, when the window opens in that monitor.  After enough time, the video fails on both monitors, and X needs to be restarted.

An annoying problem, yet you are the first person who I have seen mention the issue other than myself.

---

### Post by matthewcraig on 2007-11-13
I filed a bug report, since this issue is not isolated to my system.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/162343)

---

### Post by watermark on 2007-11-13
It's probably related, so I'll post this just in case.  I use remote connections too.  The remote connection screen used to extend onto the 2nd monitor in feisty, but after upgrading to gutsy and using the screen and graphics tool, now all I see is black.  I can't see anything on the second monitor when I'm remotely connected.

This again makes me think it's X and not the nvidia driver.

---

