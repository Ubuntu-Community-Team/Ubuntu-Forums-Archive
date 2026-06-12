---
title: "nVidia 180.22 + Compiz = Video tearing (still)"
date: 2009-02-06
forum: Multimedia Software
---

### Post by Antioch on 2009-02-06
So I installed the new (Jan 6th) nvidia 180.22 drivers tonight. I fired up a video in totem with compiz enabled -- there is still tearing.

Is there any way around this short of: disabling compiz, watching a video, re-enabling compiz? (Which is really a terrible solution)

I mean, in nVidia even aware of this problem? Is it not fixable through drivers?

It's kind of a deal breaker bug, IMO.

Any thoughts/advice?

Thanks

---

### Post by justsomedude on 2009-02-06
If you haven't done so, install compizconfig-settings-manager. Open it, and navigate to General Options --> Display Settings.

-uncheck "Detect Refresh Rate" if the wrong refresh rate is displayed below
-make sure "Refresh Rate" is correct
-check "Sync To VBlank"

Also, check General Options --> General "Undirect Fullscreen Windows"

If the above is not enough, install nvidia-settings.

Check X Server XVideo Settings:

-Video Texture Adaptor: Sync To VBlank
-Video Blitter Adaptor Settings: Sync To VBlank

..and Open GL Settings --> Performance: Sync To VBlank

In order for the changes to take effect, you have to add

```
nvidia-settings -l
```

To your autostart.

Set Video Output for your video players to either "XV" or "OpenGL".

Also, set gstreamer-properties Video Output to Xv.


This should do it, except for flash videos in your browser. Flash is crap anyway, but you can play these videos from your /tmp folder with mplayer, VLC or Totem and there should be no tearing.

There you go... :)

---

### Post by Antioch on 2009-02-06
Beautiful.

I wish I knew about the refresh-rate error earlier - that was all I needed to change to fix it. :)

Thanks for the help!

---

### Post by celem on 2009-02-06
I wish that I could say that this fixes things for me, but it doesn't. Also, yesy, you can, with some hassle, play YouTube flash from /tmp but hulu.com doesn't cache their flash there and you cannot view the files. Anyway, this hassle doesn't really make it a usable system. Poor and erratic video performance may make me go back to XP.

---

### Post by Antioch on 2009-02-06
Hmm, I guess I'm lucky then.

I just tried out Hulu and YouTube videos - I didn't see any tearing. Even tried Hulu on full screen - nothing.

Again, I just installed 180.22 drivers, that may make a difference. I also have an 8800GTX, although I'm not sure if that changes anything.

Good luck to you! I hope you figure it out so you don't have to go back to XP.

---

### Post by tanha on 2009-04-09
> **justsomedude said:**
> If you haven't done so, install compizconfig-settings-manager. Open it, and navigate to General Options --> Display Settings.

-uncheck "Detect Refresh Rate" if the wrong refresh rate is displayed below
-make sure "Refresh Rate" is correct
-check "Sync To VBlank"

Also, check General Options --> General "Undirect Fullscreen Windows"

...

There you go... :)

I've had this problem for the longest time. Just stumbled upon this solution. Works great! Thank you so much! :)

---

### Post by djwohls on 2010-03-27
Thank you, thank you, thank you!

Some of the other solutions that I found were helpful, but "check General Options --> General "Undirect Fullscreen Windows"" made it perfect.

---

