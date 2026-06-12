---
title: "Hardware for video editing"
date: 2012-01-20
forum: Multimedia Software
---

### Post by dave0109 on 2012-01-20
I'm going to build a new machine to replace my aging video editing system, and will be looking at moving it to [?]ubuntu.  I'll be looking at things like Blender to do compositing work.

Will I need to get a graphics card or will the onboard graphics from a Z68 chipset mobo with Intel i5 2500K and 4GB RAM be upto the job?

Looking for feedback from those running Blender already and how much oomph you need.  I'll be working (potentially) on full 1080p video.

---

### Post by WasMeHere on 2012-01-20
Hi Dave,

I work with full 1080p video from my camera. I am only an amateur using ***OpenShot*** for editing and ***ffmpeg*** for conversion to formats playable by our TV set as well as average computers. I have an HP xw8400 workstation with 2x2 zeon CPUs and 4 GB RAM. And I recently upgraded the graphics to / cut from the output of [FONT="Courier New"][SIZE="3"]sudo lshw[/SIZE][/FONT] /
```
            *-display
                description: VGA compatible controller
                product: GF108 [GeForce GT 430]
                vendor: nVidia Corporation

``` This hardware makes to possible use vdpau for processing. It can play 1920x1080-50p video. It is 'perfect' with VLC in Windows XP but not quite so with VLC in Ubuntu Studio 11.04. mplayer with lavd and/or vdpau plays it better but not quite perfect. I am not sure if the computer (cpu, ram or mobo) or the graphics card is limiting the playback quality.

***OpenShot*** is OK for my editing needs (I'm not sure if it uses multithreading). ***ffmpeg*** works well and takes advantage of multithreading using the zeon processors, but I don't think it uses the graphics processor. Someone reading this, correct me if I am wrong! 

I have no experience of Blender.

Have fun finding out :-)
Olle

---

### Post by ppqq on 2012-01-20
Kdenlive!!  far superior to openshot, good results, but takes some learning.

I hardly use any effects, just cutting and rendering.  its quite fast work with X to select cut, click to cut, S to get select tool, click and D to remove (my own shortcut key), right-click and R to close the gap.  Space to play/pause.

I get clear playback of MTS 1080p files with VLC but I can't get stills as VLC can't decode or something.  So I use mplayer/gnome-mplayer from the repos but of recent it freezes my session all the time.

From my understanding a grapics card will help playback, but the processor is what's important for encoding.  i5 is better than dual core, but there is 1st gen and 2nd generation i5 -sandy bridge.  This year the intel chips will be faster -ivy bridge- and 2013 even more speed is coming with thelwel chips.

---

### Post by dave0109 on 2012-01-21
Thanks guys.  I know certain edit suites within Windows will use the GPU, particularly for realtime rendering.

I think I'll suck it and see.  If the system can't cope, I can always add a video card to beef it up. :)

I've been using Adobe Premiere and AE for years, but I'm not going to pay again to get the latest versions.  Much rather contribute to a good open source project.

---

### Post by WasMeHere on 2012-01-21
> **dave0109 said:**
> Thanks guys.  I know certain edit suites within Windows will use the GPU, particularly for realtime rendering.

I think I'll suck it and see.  If the system can't cope, I can always add a video card to beef it up. :)

I've been using Adobe Premiere and AE for years, but I'm not going to pay again to get the latest versions.  Much rather contribute to a good open source project.

You are welcome :-)

---

### Post by Basher101 on 2012-01-21
i use Fraps with my new build (see sig) and i never used it before, i just wanted to make some benchmarks and recordings as tests....when i was encoding the videos, the only component that had a performance hit was the CPU. I was at 90% CPU usage on all 4 cores through the whole encoding process, my graphics card (which is pretty high-end) was not used at all in the process. I will have to look at how encoding works when using both GPUs together in Lucid Virtu (i use only my GTX 570 because some games run very sluggish when using Virtu..). 

*note: for the encoding i used Windows Media Encoder x64 Edition

If you want i will make a test or two to see how much encoding performance will increase when using both GPUs in Virtu.

regards

---

### Post by dave0109 on 2012-01-23
That would be great, thanks.  No rush though.

---

