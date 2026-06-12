---
title: "mPlayer in full screen is windowed video with black background"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by C.o.A.X on 2007-02-13
Hello,

I am trying to make the switch. So I'd like all the stuff I use on Windows to have an equivalent on Ubuntu. Nothing new to anyone I'm sure.

I am using AIGLX and mPlayer with the x11 (XImage/Shm) driver (only way I get video to display). I have a Dell XPS m1210 (intel video chipset).

When I decide to go full screen, the video gets centered but doesn't stretch to full screen. Instead the background just changes to black. Hehe. Can anyone help?


 . C o A X

---

### Post by glennric on 2007-02-13
Edit the file ~/.mplayer/gui.conf and change
```
vo_driver=???
```
to
```
vo_driver=xv
```
where ??? is whatever it is now if it is not xv.  If it is already xv then I don't know.

Edit: Actually, you can change this from the preferences in mplayer too.  Try some of the other drivers there if this doesn't work.

> **C.o.A.X said:**
> Hello,

I am trying to make the switch. So I'd like all the stuff I use on Windows to have an equivalent on Ubuntu. Nothing new to anyone I'm sure.

I am using AIGLX and mPlayer with the x11 (XImage/Shm) driver (only way I get video to display). I have a Dell XPS m1210 (intel video chipset).

When I decide to go full screen, the video gets centered but doesn't stretch to full screen. Instead the background just changes to black. Hehe. Can anyone help?


 . C o A X

---

### Post by Soulxlight on 2007-02-13
Or this worked for me. Find your config file in .mplayer in /home/username/.mplayer, and add this

```
zoom = "1"
```

That should cure your problem, if it doesn't post back ^^

---

### Post by hedonist on 2007-06-28
I m a dapper user (Kubuntu 6.06). I face the same full screen problem in mplayer and have tried the zoom="1"option in mplayer config file but when the video plays full screen the audio and video go out of sync and it sort of starts pausing. Also i m using the x11 Ximage/shm driver. Also i m using FFmpeg's libavcodec codec family  and FFmpeg/libavcodec audio decoders . Plz help!!!!!!!

---

