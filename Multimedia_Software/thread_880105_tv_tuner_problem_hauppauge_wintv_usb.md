---
title: "tv tuner problem: hauppauge wintv usb"
date: 2008-08-04
forum: Multimedia Software
---

### Post by den benne on 2008-08-04
Hey,

I've been unable to get this tv-tunercard to work:[http://www.hauppauge.com/html/usb_data.htm](http://www.hauppauge.com/html/usb_data.htm)
It's fairly old, but it does the trick under winXP. 
I believe it should be able to work, because I found old topics on this card. However, the problem then was how to install the usbvision-driver. Now, this driver is already included in the kernel, at least I think so.

when I fire up wintv, it tells me that the capture device is busy and gives me a blue screen. sometimes it even kickes me out of X !

Thanks,

Benjamin

forgot the link to the old post: [http://ubuntuforums.org/archive/index.php/t-3492.html](http://ubuntuforums.org/archive/index.php/t-3492.html)
also, I'm on ubuntu 8.04

---

### Post by den benne on 2008-08-26
still stuck on winXP...

---

### Post by wolfen69 on 2008-08-26
did you install ivtv-utils? install that then open vlc, file>open network stream>pvr tab>OK. dont know if it will work, but worth a shot.

---

### Post by den benne on 2008-08-27
> **wolfen69 said:**
> did you install ivtv-utils? install that then open vlc, file>open network stream>pvr tab>OK. dont know if it will work, but worth a shot.

sadly, this didn't work

---

### Post by ktp on 2008-09-11
I been playing around with this most of today and here is what I got:

I have it working in mplayer so if you don't have it installed then 
```
sudo apt-get install mplayer
```

Connect the WinTV USB.  Hardy already has the drivers needed for this issue following command to view TV:

```
mplayer tv:// -tv driver=v4l2:immediatemode=0:norm=ntsc:chanlist=us-cable:outfmt=yuy2 -vo gl2
```

You can change norm=ntsc to pal if that is what you need.  To change channel use 'h' and 'k' keys.

Hope it works!!

---

### Post by CrazyMordeAFoca on 2009-12-10
It worked...but only in black and white...

---

