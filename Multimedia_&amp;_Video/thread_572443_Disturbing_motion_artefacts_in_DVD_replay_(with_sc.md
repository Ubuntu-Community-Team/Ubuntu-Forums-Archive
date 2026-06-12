---
title: "Disturbing motion artefacts in DVD replay (with screenshot)"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by tbraun on 2007-10-10
Hello!

Hope you can help me. I just recently got a DVD camcorder, and I'm now trying to replay the recordings I made. Sadly, whenever there is motion in the picture, I get very odd artefacts. If the picture is mostly still, those artefacts are not visible.

I have attached a small portion of a screenshot from a scene. This is during a slow pan of the camera. In all the vertical lines you can see the distortions. If the camera holds still, those distortions disappear. If a person walks through an otherwise still picture, only the person shows the distortions.

This happens if I play it with Totem, or with VLC, ... it doesn't matter what application. So, I assume it's a codec problem? I got the codecs the usual way, through Automatix.

I booted into my Windows partition, and there it plays without any artefacts. So, now I really would like to be able to fix that for Linux as well.

For what it's worth, I use Feisty on a Dell Latitude D820, 2GBytes with some laptop-ish Nvidia card and a GeForce Go 7400 driver. In every other respect, I have no problem at all with the graphics on this machine.

Any help would be greatly appreciated...

Tom

---

### Post by rsambuca on 2007-10-10
It is artifacts due to the interlaced video.  If using vlc, activate your deinterlacing option and set it to blend.

---

### Post by tbraun on 2007-10-10
> **rsambuca said:**
> It is artifacts due to the interlaced video.  If using vlc, activate your deinterlacing option and set it to blend.

Ah, that helps. Thank you very much for that very quick response!

Actually, 'Linear' seems to give better results than 'Blend'. But how can I have that done by default? VLC doesn't seem to remember the settings. Besides, VLC is not the default for those files anyway. I normally use Totem. But I find that Totem's de-interlacing doesn't seem to be as nice as VLC's (in Linear mode). Any suggestions on how Totem's de-interlacing could be improved?

But this is definitely a huge help already. Thank you again...

Tom

---

### Post by rsambuca on 2007-10-10
I am sure there must be a way to use Totem for this, but like you I get crappy results, so I have just always used vlc.  In vlc, you just go to "Settings > Preferences > Video > Filters (Advanced Options).

---

### Post by tbraun on 2007-10-10
> **rsambuca said:**
> I am sure there must be a way to use Totem for this, but like you I get crappy results, so I have just always used vlc.  In vlc, you just go to "Settings > Preferences > Video > Filters (Advanced Options).

One other problem that I have (just shows that I'm a total noob with this) with Totem as well as VLC is this: If I copy the contents of the DVD to my HD, I cannot use the DVD menu anymore. In both Totem and VLC I can say 'play disk' when I still have the DVD in the CD/DVD-drive, and it recognizes the menu file, let's me click on chapters and such. All is good. But once I copy it all to HD, I can't do this anymore. The file that contains the menu is just treated like any other video file, It's played (usually only lasts a second or so) and there is no way to click on any chapter. Is there a way to tell those programs to treat some directory like it would be the disk itself?

Any hint would be greatly appreciated.

Thank you very much...

Tom

---

### Post by rsambuca on 2007-10-10
> **tbraun said:**
> One other problem that I have (just shows that I'm a total noob with this) with Totem as well as VLC is this: If I copy the contents of the DVD to my HD, I cannot use the DVD menu anymore. In both Totem and VLC I can say 'play disk' when I still have the DVD in the CD/DVD-drive, and it recognizes the menu file, let's me click on chapters and such. All is good. But once I copy it all to HD, I can't do this anymore. The file that contains the menu is just treated like any other video file, It's played (usually only lasts a second or so) and there is no way to click on any chapter. Is there a way to tell those programs to treat some directory like it would be the disk itself?

Any hint would be greatly appreciated.

Thank you very much...

Tom
Sorry, no idea on the DVD menus.

---

