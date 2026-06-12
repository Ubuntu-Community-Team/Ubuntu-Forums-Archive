---
title: "I can finally play AVCHD (using latest VLC) !!"
date: 2008-12-31
forum: Multimedia Software
---

### Post by bsmith1051 on 2008-12-31
Have I finally managed it? Can I finally watch my Sony HD camcorder recordings on my Ubuntu home computer?? Still need to try this on my main system (which is faster) but I can finally play them without crashing! Here's how I did it:

**PROCEDURE**

[LIST=1]
[*]Tested on an Athlon X2 dual-1.9Ghz machine running Ubuntu 8.10
[*]I uninstalled _all_ existing 'vlc' components (which were v0.9.4) through Synaptic
[*]I also had to delete the ~/.config/VLC configuration files
[*]Per the instructions on the Videolan.org site I added their "Intrepid/Nightly" repository to Synaptic,
[http://nightlies.videolan.org/#debian](http://nightlies.videolan.org/#debian)
[*]I installed the latest version, v1.0.0~git20081127-4 (according to Synaptic)
[*]I then disabled the Videolan repository since this copy seems to be working!
[*]Finally, I disabled the FFMPEG "h.264 Loop Filter" in VLC (this improves playback speed but at the cost of some picture quality),
[http://forum.videolan.org/viewtopic.php?f=2&t=42328](http://forum.videolan.org/viewtopic.php?f=2&t=42328)
[/LIST]
My Sony's AVCHD clips are 1440x1080i and this computer (using one 1.9 GHz cpu-core at 100%) can't quite play it back without dropping frames. BUT **it doesn't crash anymore**, which every other video player (including previous versions of VLC) would do! So now I'm hopeful that my other system will be fast enough...

P.S. I'm being very specific about uninstalling all the original 0.9.4 modules, as well as deleting the hidden config folder, because both of those elements caused errors otherwise!

---

### Post by bsmith1051 on 2009-01-01
Indeed, I can now play my AVCHD clips and without any dropped frames! :)

My main computer is Ubuntu 8.10 on an AMD dual-2.7 GHz, and I still have to disable all the h.264 'loop filters'.  Also, the VLC 'nightly' has lots of interface quirks that the 0.9.4 'stable' doesn't.  The only significant one is that I can't enable the option for "Allow only one instance" else the program won't load, at all.

---

### Post by sierramike on 2009-02-20
Hi bsmith1051, thanks for your story, I will try this !

I have actually an HTPC setup with MythBuntu and cannot play AVCHD clips, nor any H264 video clip I would get from an editing software.

Actually I'm willing to play these kind of clips (I downloaded short AVCHD videos on forums so I can test before I buy such a camcorder).

My system is C2D 2.53GHz with Geforce 7300/128Mo, do you think it can be enough ? Should I change the graphics card or won't that improve anything, as I think Linux doesn't use actually NVidia hardware H264 decoding ?

Any way to have VLC or another player use the 2 cores for decoding video ?

---

### Post by bsmith1051 on 2009-02-20
I think your CPU is plenty capable, even on just one core.  Unfortunately there are no solutions on Linux for using both cores, and the videocard hw-acceleration is still experimental (and only supported on the newest generation of cards, e.g. Nvidia 9300+)

I'm not that familiar with Mythbuntu -- what's the default player?  if it's Totem (or Mplayer) then the h.264 support is minimal.  I think you just need to setup VLC and make it the default app for the file-types you're testing.

Finally, I wouldn't hesitate to buy a new AVCHD camcorder.  The software will eventually come around!  I went through this same experience with both MPEG2 and MPEG4 over the past decade or so.  Now there's VideoRedo, VirtualDubMod, etc.

---

### Post by sierramike on 2009-02-20
Okay, thanks for your help ...

Yes the default player is mplayer, and I didn't try VLC as the windows version installed on my laptop (C2D 2.27 GHz/ATI HD3430) plays approx 1 frame per 2 second on AVCHD files ... So I thought VLC would be the worst player ... But I'll give it a try !

Very bad that no multicore solution exists on Linux, I expected that those things would much more optimized on Linux than on Windows, knowing what everybody says about Linux ... And multicore CPUs exists since a few years now ...

Anyway, I'll try VLC and let you know.

Otherwise, is there an easy way to convert the files into another format that would play better on my harware ?

For information, on the "Freebox" which is a ADSL provider in France, I can put AVCHD on the internal HDD as it comes out from the camcorder, and it plays very well ! Since it is linux-like based box, I hoped their player would be opensource and installable on other Linux systems.
(The Freebox solution would not be good to me as it is not stable, and the HDD is very small ...)

---

### Post by cotcot on 2009-02-20
I can play them using mplayer (svn) :

```
mplayer -demuxer lavf -lavdopts threads=4:fast:skiploopfilter=all:skipframe=none -fps 25 -vf pp=lb  myvideo.MTS

```

---

