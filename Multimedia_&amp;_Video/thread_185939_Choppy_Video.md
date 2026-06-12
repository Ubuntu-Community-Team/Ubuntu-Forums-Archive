---
title: "Choppy Video"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by seanUSXIII on 2006-06-01
Recently I have been having a problem with video on my computer being slightly choppy. Its just barely bad enough to make me want to boot into windows to watch a dvd. I'm using the dapper beta 2, as I haven't had a chance to dist-upgrade yet. This is not only with mplayer, but totem and xine as well. At first I thought it was frame-dropping, but I ruled that out by turning it off. Then I thought, maybe Compiz is screwing it up, but after rebotting withouth Compiz (with XGL still on, however), the problem is still there. I've noticed Compiz has been a bit choppy, too. Could this be my nvidia driver? I havent got any updates lately, so when I get my serial modem sometime soon, I'll update and see. Has anyone else seen this?

---

### Post by berdoo on 2006-06-01
I had the same problem and had to disable Xgl as well as Compiz to get smooth playback. WMV videos were also looking strange.

My video card is quite old though (64 MB GeForce 3) so that may be the problem, although the effects (wobble, cube, etc.) worked very smoothly.

---

### Post by cptgrudge on 2006-06-01
I had the same problem.  Everything was fine in Breezy, but when I upgraded to Dapper (and installed xgl and compiz), it started having problems with playing video.  I've got the same type of card (GeForce 3 64MB) and the new effects work fine and smooth.  Just the video has a problem.  :rolleyes: 

Removing glx and compiz would probably do it for me too, but I'm not sure I'm ready to give it up quite yet.  :(

At least we're not alone.

---

### Post by chameleon_789 on 2006-06-01
I've had some trouble with choppy playback from DVD's, after some fishing around I fixed it by enabling DMA on my drive... in a terminal type :
*sudo hdparm /dev/hdc* - (replace hdc with your cddrive, should be dev/hd*, you can find out what it is in /etc/fstab), you'll get an output like :
```
root@chameleon-ubuntu:/home/chameleon# hdparm /dev/hdc
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
```

If the 'using_dma' flag is off, use : *sudo hdparm -d1 dev/hdc*(or your drive) to turn it on, and DVD playback should be alot smoother. I think there are some instructions on [this]("http://www.vmware.com/support/reference/linux/host_perf.html") website on how to make it permanently use DMA .

---

### Post by cptgrudge on 2006-06-01
Looking around, this thread might show what the problem is.

[http://www.ubuntuforums.org/showthread.php?t=143265](http://www.ubuntuforums.org/showthread.php?t=143265)

It seems that it will be supported in "the near future", but that video playback gets put into a slower version for now.

---

### Post by chameleon_789 on 2006-06-01
oops, doublepost :|

---

### Post by cptgrudge on 2006-06-01
After messing around with settings for a while, I've found a solution that works for me at least.  I stopped using totem as my video player and started using mplayer instead.  In mplayer, under Preferences, Video it defaults to using the xv driver, and has about the same level of performance as totem.

I can switch it to "x11 (XImage/Shm)" with direct rendering and frame dropping enabled (and without the ability to resize the window) or to gl2 also with direct rendering and frame dropping enabled.

Those seem to give better performance.  My CPU is rather lacking in this computer, and I can see that the xgl process eats a lot of CPU time when I'm playing a video through totem.  With a faster processor, the problem would probably go away, I imagine.  Mplayer does seem to die sometimes, but I can live with that.  For now, I've got both the acceptable video and the snazzy effects.  :D 

I'd seen posts around that said that mplayer was better than totem.  Guess I'm a believer now.

---

