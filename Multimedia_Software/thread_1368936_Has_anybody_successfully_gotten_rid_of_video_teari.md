---
title: "Has anybody successfully gotten rid of video tearing?"
date: 2009-12-31
forum: Multimedia Software
---

### Post by Roasted on 2009-12-31
Because I haven't. It's been an ongoing battle for years. As much as I like VLC, VLC is the one program that does it the most. I've changed all kinds of settings on it, blah blah blah.

What seems to work better is when I switched to Kubuntu and found "Dragon Player" pre-installed. It played my videos on my 19" monitor with NO tearing. Once I move it to my 24" monitor I get some tearing, but it's 98% better than VLC.

But, alas, it still exists. Using 185 drivers. Nvidia 9600GT. Dual monitors -  VGA 19 1440x900 - DVI 24 1920x1080.

---

### Post by lovinglinux on 2009-12-31
Yes, but I guess you have already tried my solution.

---

### Post by Roasted on 2009-12-31
Link to your solution, perhaps?

---

### Post by lovinglinux on 2009-12-31
> **Roasted said:**
> Link to your solution, perhaps?

[http://ubuntuforums.org/showpost.php?p=7950332&postcount=2](http://ubuntuforums.org/showpost.php?p=7950332&postcount=2)

---

### Post by Roasted on 2009-12-31
I assume with me playing around in KDE land I can do the same changes there with expected good results?

---

### Post by lovinglinux on 2009-12-31
> **Roasted said:**
> I assume with me playing around in KDE land I can do the same changes there with expected good results?

I'm in KDE too. Nevertheless, I have applied the xorg changes only in Jaunty. They didn't work on karmic and I had to login with a liveCD and delete /etc/X11/xorg.conf to go back to the previous settings. So, I would recommend skipping the xorg configuration.

---

### Post by LuisGMarine on 2009-12-31
Cool I was just about to say I your fix in Karmic and nothing happened.  I have Jaunty on this laptop so I'm going to give it a try and post back later.  Seems like an awesome fix.

---

### Post by Fire_Chief on 2009-12-31
Would you happen to be running visual effects? I found that if I play video with them enabled I would get tearing. Turned them off and video was perfect.
Just a thought.

Cheers!

---

### Post by LuisGMarine on 2009-12-31
wow I feel dumb I never did try to play videos with video effects disabled.  So let me give that a try.

---

