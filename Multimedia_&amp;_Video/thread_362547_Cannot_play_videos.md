---
title: "Cannot play videos"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by RotoGrip on 2007-02-15
Hi all,

 Im unable to view some movies online using firefox. Heres a good example [http://ourworld.compuserve.com/homepages/kennmelvin/VSoccer.Htm]("http://ourworld.compuserve.com/homepages/kennmelvin/VSoccer.Htm")

Any hope to geting this to work?

---

### Post by Arlanthir on 2007-02-15
I'm using firefox 2.0.0.1 on Edgy Eft and I can't see most of flash clips too, including those on [www.break.com]("http://www.break.com") (I am presented with a 'get flash' button).
I have installed the plugin a million times already (read: 4 or 5) and I got no solution.

I can, however, watch youtube videos... Aren't those flash too?
Just adding my noob-experience here.

---

### Post by r4ik on 2007-02-15
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

or,

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

or,

[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29)

Good luck !

---

### Post by r4ik on 2007-02-15
> **Arlanthir said:**
> I'm using firefox 2.0.0.1 on Edgy Eft and I can't see most of flash clips too, including those on [www.break.com]("http://www.break.com") (I am presented with a 'get flash' button).
I have installed the plugin a million times already (read: 4 or 5) and I got no solution.

I can, however, watch youtube videos... Aren't those flash too?
Just adding my noob-experience here.

Try,

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

Good luck !

---

### Post by vigleik on 2007-02-15
Wait, aren't we getting off topic here? RotoGrip wasn't asking about flash, but about movies that present themselves in firefox as application/x-mplayer2, for which firefox is unable to find an appropriate plugin.

I would like to know the answer to this question too, though I suspect that my inability to do so has something to do with using the 64bit version of ubuntu and a standalone version of the 32bit version of firefox. RotoGrip, did you try to install....what's it called, mplayer-plugins-mozilla, or something like that?

---

### Post by RomeReactor on 2007-02-15
Hi. RotoGrip, i just saw that video. Are you running Ubuntu 32-bit or 64-bit? If you're on 32-bit Edgy, is **mozilla-mplayer** your Firefox video plugin? If not, maybe you should use it; it's probably the best video plugin for FF i've seen. Just make sure you uninstall all the other plugins (helix, totem, realplayer, vlc) before installing mozilla-mplayer. A search for Mozilla in Synaptic will tell you which ones you have installed. Also, you'll need the w32codecs; for those you need to have the PLF repositories, if i'm not mistaken: To see if you do have them, try in a terminal

```
gksudo gedit /etc/apt/sources.list
```

enter your password and look for this entry

```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

Add it at the end of the file if it's not there; then Open synaptic, click reload and search for **w32codecs**.

---

### Post by RotoGrip on 2007-02-15
Rome,

 Thanks for the help. It works great now. 

Arlanthir, use the link in R4ik's second post my flash now works as well.

 Thanks again for the help guys

---

### Post by Arlanthir on 2007-02-16
Yes, all problems solved =)
Thank you all very much!

---

