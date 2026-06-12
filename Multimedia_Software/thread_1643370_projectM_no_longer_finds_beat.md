---
title: "projectM no longer finds beat"
date: 2010-12-11
forum: Multimedia Software
---

### Post by arpad9 on 2010-12-11
I found projectM-pulseaudio and easily installed it from the Ubuntu repository (running 10.10). I happened to have Pandora running when I started it up and it JUST WORKED. SO COOL!!! 

Later, I plugged in a USB headset so the pulse outputs changed around and it stopped working. I haven't been able to get it to work ever since. I see it in "Volume Control" as a recording device. I see it in PulseAudio Manager as a client. I've double checked the PulseAudio preferences in ProjectM and everything seems correct. 

I just can't get ProjectM to pick up beats anymore. It doesn't spit out errors when run from the command line. I'm kinda stumped. I knew it was too good to be true.

---

### Post by ridetheteapot on 2011-01-22
press 'm' to get the menu and then go to settings -> pulseaudio settings then uncheck use 1st monitor and select the output monitor of the usb headset, shouldnt be many choices - one that says output.

---

### Post by arpad9 on 2011-01-22
If only it were that easy.

I appreciate the reply though, thank you.

---

### Post by ridetheteapot on 2011-01-22
bummer, i have a usb soundcard that works fine like that, but i dont have a usb headset to try out.

---

### Post by arpad9 on 2011-01-23
So... as per this thread,
[http://gnome-look.org/content/show.php?content=99383&forumpage=13&PHPSESSID=6](http://gnome-look.org/content/show.php?content=99383&forumpage=13&PHPSESSID=6)

listing the sources via:
```
pacmd list-sources
```
and then unmuting the appropriate source via:

```
pacmd set-source-mute 1 0
```
did the trick.  Where 1 is the number of the source (beginning with 0) and 0 is the value (muted=0).

I don't know where this value shows up in any gui control interface and I'd argue that it doesn't but this command did the trick for me.

---

### Post by ridetheteapot on 2011-01-24
nice its working projectm is awesome. The package from the ubuntu repos isn't compiled with cg shaders activated.

if your gfx card supports shaders i HIGHLY recommend recompiling with USECG and grabbing some milkdrop presets that use shaders. (ryan geiss, the dude who wrote milkdrop has a collection of favorites at his website [http://www.geisswerks.com/about_milkdrop.html](http://www.geisswerks.com/about_milkdrop.html))

---

