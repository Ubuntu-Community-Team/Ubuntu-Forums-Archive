---
title: "Video settings work with nvidia-settings, but not kept in xorg.conf"
date: 2013-04-30
forum: Multimedia Software
---

### Post by PoDuck on 2013-04-30
I have been having trouble with this for weeks now.  I had settled on 1280x720 resolution, but I lose way too much screen real estate, so I'm trying to get my settings for 1920x1080 to work, but whenever I reboot or logout, I lose them.

DFP-1 is my television hooked up through HDMI, DFP-2 is my regular monitor.  The television doesn't have a setting to stop the overscan issue, so I have to do it this way.

I can set my resolution perfectly if I use nvidia-settings.
```
nvidia-settings --assign 0/CurrentMetaMode="DFP-1: 1920x1080 +1920+0 { ViewPortIn=1920x1080, ViewPortOut=1800x1012 +60+34 }, DFP-2: 1920x1080 +0+0"
```

Unfortunately though, I can't get the settings to stick by putting them in xorg.conf.

Excerpt from /etc/X11/xorg.conf:
```
Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-1: 1920x1080 +1920+0 { ViewPortIn=1920x1080, ViewPortOut=1800x1012 +60+34 }, DFP-2: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

This is exactly the same settings as used in the nvidia-settings command.  I copied and pasted them from the command line.

When I use the same method to set things for 1280x720, I have no trouble at all with this.

When the screen comes up, the television says it's in 720p instead of 1080p, but when I enter the nvidia-settings command the television says it is in 1080p.  Also, the screen resolution on the regular monitor is 720p, but everything shows up there correctly.

---

### Post by PoDuck on 2013-05-02
Odd.  No replies in 2 days.  I would have assumed this to not be a totally unheard of problem.

Needless to say, I decided to try 13.04 to see if this issue was fixed, and that was a total fiasco.  I reinstalled 12.10, put that same metamodes option in xorg.conf, and all is great now.

If I had to guess, now that all evidence of my probable stupidity has been destroyed, I would say that the problem was likely that I had somehow gotten a personal video setting set in my home folder that screwed things up by overriding the xorg.conf setting, because I was having no video issues when logged out.

Needless to say, I was doing things correctly in what I put in the OP.

---

