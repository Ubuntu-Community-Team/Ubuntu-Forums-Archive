---
title: "How do I get rid of page tearing?"
date: 2009-11-24
forum: Multimedia Software
---

### Post by lakersforce on 2009-11-24
It happens all the time I watch videos, making video watching a not so enjoyable experience on GNU/Linux.

I have an LCD monitor with a resolution of 1440x900, with a (system) refresh rate of 59.86. My preferred video player is VideoLan VLC.

---

### Post by Melcar on 2009-11-24
What video card?  If its ATI and you're using fglrx then you're out of luck; no real way of fixing it.  Some say that using opengl as your video output and enabling vsync in amdcccle resolves it, but for me it never does.  Open source ATI drivers have tear free video playback, but you may or may not want to use those.
If its nvidia, then I have no idea.

---

### Post by lakersforce on 2009-11-24
I have a Nvidia GTX 260 card. I tried enabling the "Sync to Vblank" under openGl settings in the "Nvidia X Server Settings" program, but it did no difference (after restart.)

---

### Post by mc4man on 2009-11-24
While i think it's a combo of model specific display adapter, driver version, ubuntu release, and compiz, for all of our nvidia based setups tearing has been completely eliminated by (kitchen sink approach

enabling sync to v in both 'X server XVideo' and 'OpenGl' in nvidia setting

Also in CompizConfig Settings Manager under the general options tab -> Display Setting

Additionally in  CompizConfig General tab unchecking the "unredirect fullscreen windows'

If you're on karmic, after changing these I'd reboot, karmic has some oddities in that regard

---

### Post by lakersforce on 2009-11-24
> **mc4man said:**
> 
Also in CompizConfig Settings Manager...

Where do I find that?

---

### Post by mc4man on 2009-11-25
> Where do I find that? 

```
sudo apt-get install compizconfig-settings-manager
```

Then look in System -> preferences -> CompizConfig.....

( one of a few area's where default settings have been predetermined yet an easy way to adjust isn't provided

---

### Post by lakersforce on 2009-11-25
Ok, did it. Still the same horrible page tearing, both when watching video in windows and fullscreen.

---

### Post by Arup on 2009-11-25
Use latest 190.42 drivers, I have absolutely no tearing either using mplayer with vdpau or vlc with my cheap 8400GS nvidia.

---

### Post by lakersforce on 2009-11-25
> **Arup said:**
> Use latest...drivers

I am. But I would rather not use mplayer. I know it is possible to set it up without pagetearing with some rather elaborate flags in mplayer, but I would like to use VideoLan VLC.

---

### Post by lakersforce on 2010-01-24
I completely disabled all desktop effects and that solved the problem.

---

