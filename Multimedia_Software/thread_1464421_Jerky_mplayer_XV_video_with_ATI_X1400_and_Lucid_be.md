---
title: "Jerky mplayer XV video with ATI X1400 and Lucid beta"
date: 2010-04-28
forum: Multimedia Software
---

### Post by heng on 2010-04-28
I've been experiencing seriously jerky (ie, unwatchable) video since a recent update to Lucid (I'm not sure when exactly). This is using mplayer and the open source ATI driver on an dell Inspiron 9400 with a Radeon X1400 card.

The jerkiness occurs when the scaling of the window is above a certain size (so fullscreen is bad).

The videos play perfectly with "-zoom -vo x11" options, ie with software scaling and raw x11 output, which is a little crazy.

I don't even know how to begin debugging this, so any pointers would be appreciated.

Cheers,

hen

---

### Post by oyvinst on 2010-04-28
Experiencing exactly the same issue with Xv on Ubuntu Lucid (installed from RC, fully up to date). ATI X1400 mobile, KMS and using Compiz. Sometimes videos play fine in fullscreen, and other times it gets very jerky and slow, dropping a lot of frames (even very small videos scaled up to fullscreen). Maybe dependent on graphics memory pressure, since it seems to happen more often when there are many windows open. A workaround is to disable fullscreen redirection in Compiz, but I was kinda hoping to avoid that. Other slowness can sometimes be observed as well, like scrolling in Firefox or Evince document viewer. This sucks, since KMS is rather nice and stable, except for these hiccups which make many fullscreen apps unusable at times. :(

---

### Post by heng on 2010-04-29
Do you just get this with Mplayer? I seem to have found that vlc plays videos well. I'm not sure if this is some peculiarity of vlc or Mplayer or just me being poor with my experiment controls.

---

### Post by oyvinst on 2010-04-30
> **heng said:**
> Do you just get this with Mplayer? I seem to have found that vlc plays videos well. I'm not sure if this is some peculiarity of vlc or Mplayer or just me being poor with my experiment controls.

VLC perhaps plays a *little* bit smoother than MPlayer or Totem, but far from normal. Fullscreen apps with radeon KMS and composite-redirection just seem to suck badly at times, unfortunately. Perhaps there will be some updates to the graphics stack (kernel, DRI/Mesa or Xorg radeon driver) which will remedy these performance problems. But I wouldn't get my hopes up.

---

### Post by heng on 2010-04-30
> **oyvinst said:**
> VLC perhaps plays a *little* bit smoother than MPlayer or Totem, but far from normal. Fullscreen apps with radeon KMS and composite-redirection just seem to suck badly at times, unfortunately. Perhaps there will be some updates to the graphics stack (kernel, DRI/Mesa or Xorg radeon driver) which will remedy these performance problems. But I wouldn't get my hopes up.

Yeah, its a bit rubbish. Still, the mplayer -zoom -vo x11 workaround works pretty well for me.

---

### Post by curlingmonster on 2010-04-30
> **oyvinst said:**
> VLC perhaps plays a *little* bit smoother than MPlayer or Totem, but far from normal. Fullscreen apps with radeon KMS and composite-redirection just seem to suck badly at times, unfortunately. Perhaps there will be some updates to the graphics stack (kernel, DRI/Mesa or Xorg radeon driver) which will remedy these performance problems. But I wouldn't get my hopes up.
 
I'm having exactly same symptoms with HD 3650 using "10.04lts final" Will try Hengs' soloution.

---

### Post by olmari on 2010-05-08
Afaik situation is same with, say, fullscreen game, like World of Goo...

While with earlier Ubuntu distro's I could play WoG with very smooth framerate, with lucid framrate is kinda jerky, just like fullscreen videos sometimes..

So I think they're related to same rootissue...

Using radeon with compiz...

---

### Post by Rustopholous on 2010-05-09
I'm having the same issues... running anything in fullscreen.  Whether it's XBMC, World of Goo... you name it.   I'm running an Acer Aspire 5672 with an ATI Radeon Mobile X1400.  I just upgraded to 10.04 from 9.04 and never had any of these problems running the previously mentioned with it. :(

I might go back to 9.04 I guess...

---

### Post by Teroc on 2010-05-10
I have the same problem here. I could play 720p videos without too many problems with 9.10, then I updated to 10.04 and I can't even watch an SD video. When I try to set the video to fullscreen, there is no upscaling and a lot of graphics weirdness... 
ATI X1400 on my old toshiba laptop. I'll have to go back to 9.10 I guess.

---

### Post by enchesss on 2010-05-10
The open source ati drivers are much better than proprietary (with what I have tried)

i could not get anything to play full screen until i used open source divers. then just a slight stutter until a fresh install without any proprietary drivers at all.

i do have to blacklist intel drivers though - pain in the a

I put this post

[http://ubuntuforums.org/showthread.php?t=1477642](http://ubuntuforums.org/showthread.php?t=1477642)

because after a fresh install (better to not have any flgrx) i had a minor byt tricky to solve problem with totem

anyway - hope this helps:

---

### Post by lostinberlin on 2010-09-13
Hi,

might not be what you're looking for but here's my 'long sought after  and highly satisfying' solution - depending on your priorities.

Turn off "desktop effects". It's as simple as that. If you can't live  without them, you could find a shortcut to turn them on or off at will,  but I am quite happy without them and the video play back is fantastic.

There you have it. Hope someone finds this useful. Please post elsewhere  and spread the word if it worked for you so that others may get the  benefit. It took a long time to realise the connection.

Stats:
Kubuntu 10.04 (64-bit)
Thinkpad W510 (1920 x 1080)
NVidia Driver: 256.44

---

### Post by heng on 2010-09-13
better solution:

upgrade to Maverick... :)

---

