---
title: "MP4 video playback jitters"
date: 2011-01-12
forum: Multimedia Software
---

### Post by HDave on 2011-01-12
I have a collection of MP4 files that I pulled off my Samsung video camera.  However, playback of these files in totem is so stuttered it is unwatchable.  Playback in VLC is still jittery and pixelated.

If I run mplayer from the command line, it is ok...not great.  But I really want to use VLC or Totem.

Here's what mp4info reports on these files:

```

mp4info version 1.6
HDV_0006.MP4:
Track	Type	Info
1	video	H264 Main@4.2, 83.016 secs, 17019 kbps, 1920x1080 @ 59.940252 fps
2	audio	MPEG-4 AAC LC, 83.029 secs, 128 kbps, 90000 Hz
```

Any idea what will fix this?

---

### Post by BicyclerBoy on 2011-01-12
More CPU power ..& maybe PCIe graphics card.
1080p60 will be very CPU intensive & there is a lot of data to shift into GPU.

Or if using nvidia GPU you can build mplayer/vlc with vdpau support.

There is VAAPI support starting to appear so there could be some h/w decode support on other GPU platforms.

---

### Post by no2498 on 2011-01-12
try installing smplayer type it in a terminal it tells you how to install it
it helps me with mp4's

---

### Post by HDave on 2011-01-12
> **no2498 said:**
> try installing smplayer type it in a terminal it tells you how to install it
it helps me with mp4's

Tried it...no effect.  Very cool player however...

---

### Post by HDave on 2011-01-12
> **BicyclerBoy said:**
> More CPU power ..& maybe PCIe graphics card.
1080p60 will be very CPU intensive & there is a lot of data to shift into GPU.

Or if using nvidia GPU you can build mplayer/vlc with vdpau support.

There is VAAPI support starting to appear so there could be some h/w decode support on other GPU platforms.

It's a intel quad core 2.7Ghz with 8GB of RAM.  Its an Intel video adapter and I can't recall the model right now, but it handles all manner of video games and graphics at 1920x1200 without breaking a sweat!   Gotta be something with the codec...

---

### Post by BicyclerBoy on 2011-01-12
Could be..or video driver..
My core2duo can easy playback 2x1080i H264AVC.
One on the CPU ~50% & one in GPU vpdau.
Both full screen on diff X screens.

i5 or i7 then ? Are you using the integrated i5/i7 GPU ?
What GPU driver do you use with this?

I had bought an i5-750 because it had no GPU.
 
Your CPU has more threads but you need multi-threaded codec to take max advantage.

Observe the system monitor CPU loads & check if only one CPU core is maxed out.

---

### Post by HDave on 2011-01-12
Just to be sure, I also tried it out on another box I have which is an 8 core 2.7GHz AMD with an nVidia 285 card.  It's a super box and I still get the same stutter!

Edit: I dual booted my quad-core box under Windows and (I am sickened to report that) Windows media player 11 plays these files smooth as silk.

---

### Post by HDave on 2011-01-12
> **BicyclerBoy said:**
> Your CPU has more threads but you need multi-threaded codec to take max advantage.

Observe the system monitor CPU loads & check if only one CPU core is maxed out.

Great idea -- As it turns out, one of my four cores is totally maxed out.

How do I get a multi-threaded codec to play these HD files?

Edit:  GPU is an 82G33/G31 Express Integrated Graphics Controller

---

### Post by BicyclerBoy on 2011-01-13
VLC comes with everything.

I think the problem is to do with the files themselves.
Try running them thru' ffmpeg to remux them.

VLC should be multi-threaded ? But maybe  s/w decode thru' ffmpeg is not.
Build from source to get the latest but I have never needed to.

That G31 chipset is a dog..Lots of SATA HDD-optical drive problems etc.
That GPU can do full h/w decode of MPEG-2 only.

The correct driver will help with video overlay presentation etc.
What driver are you using ?

The nvidia 285 is a good gaming/openGL card but not feature set C, not so good for video.
This card with nvidia driver should have no problem with MPEG-4/10 H264AVC and the like. It's de-interlacing scaling denoise & sharpen are not as good as GT220/240/430. 

Can you provide a short sample of video of the wall/carpet/dog ?

---

### Post by no2498 on 2011-01-13
would this help him in any way


The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by BicyclerBoy on 2011-01-13
That only effects gstreamer apps like cheese & totem & rhythmbox AFAIK.

Both are not involved here..

---

### Post by HDave on 2011-01-13
@BicyclerBoy -- Thanks so much for all the help. 

While my graphics card isn't all that hot I installed Windows XP (dual-boot) and found out that Window Media Player 11 plays these MP4 files smooth as silk.

Frustrated, I did some more research and found that you are correct -- VLC is multi-threaded, but ffmpeg is not.  There is an ffmpeg-mt project that is almost ready to be released and if you compile your own VLC on top of it you can make it work, but I don't have that kind of time!

However, I also discovered that the latest version of the single threaded ffmpeg is a big improvement over what Ubuntu has in the repo for 10.04.  Following the instructions [located here]("http://www.gogogeekboy.com/2010/09/getting-h264-video-capability-into-lucid/") I installed it and at least now VLC isn't stuttering anymore.

Finally, I also discovered that if I set my camera to 720p instead of 1080i, I lose some resolution, but my new VLC plays these MP4s smooth as silk.

@no2498 - I tried changing that in gstreamer-properties but it had no effect.  I've totally given up on totem being able to play these. :(

---

### Post by HDave on 2011-01-13
@BicyclerBoy -- How do I find out what video driver I am using?  I ran "Hardware Drivers" and it says there are no proprietary drivers in use on the system and offers up none either.

Will try recoding with ffmpeg shortly....

---

### Post by BicyclerBoy on 2011-01-14
Please post your /etc/X11/xorg.conf &  /var/log/Xorg.0.log ?
This should reveal something..

Post the output from
lsmod | grep intel
lsmod | grep video

If the xorg.conf is missing this is a clue..

Windows almost always has/gets the proprietary driver.
Intel made sure their drivers get the most out of their crappy GPUs.
So windoze will maximise the video performance of intel c.f. linux.

If you want video performance with Linux then nvidia is the only sensible way.

---

