---
title: "AMD video acceleration (mythbuntu 12.04)"
date: 2012-04-29
forum: Mythbuntu
---

### Post by odror on 2012-04-29
I would like to switch from nvidia to amd video card (I need more than a 2 monitors support).

Is video acceleration supported by mythtv. On the playback profiles I only see VPDAU. I do not see VAAPI or the AMD equivalent.

Is there an issue with video tearing.

Thanks

---

### Post by nickrout on 2012-04-29
> **odror said:**
> I would like to switch from nvidia to amd video card (I need more than a 2 monitors support).

Is video acceleration supported by mythtv. On the playback profiles I only see VPDAU. I do not see VAAPI or the AMD equivalent.

Is there an issue with video tearing.

Thanks

vaapi is available in 0.25. However AMD cards are far inferior to nVidia for HTPC.

---

### Post by odror on 2012-04-29
> **nickrout said:**
> vaapi is available in 0.25. However AMD cards are far inferior to nVidia for HTPC.

1. How do you enable the VAAPI profile.
2. Why nvidia is inferior. All I am interested is to see videos (mp4 and mp2). I am not interested in games.
3. I have two pci-express x16 slots. Can I have ATI and Nvidia on the same machine? I have tried it 6 months ago. it did not work. Is it OK now in 12.04.

The problem that I am having is that I need to have 4 monitors (one is HDTV). I have heard that eyefinity (ati) works for linux. Xinerama works without compiz. (thus no gnome 3 or unity 3d)

Thanks

---

### Post by superm1 on 2012-04-29
1)
So I haven't actually used it before - but you need to install "xvba-va-driver".  It's the AMD VA API driver package.  I don't believe it's pulled in by default.

2) NVIDIA's VDPAU video acceleration is far more mature and stable at this point.  I would say a majority of MythTV Linux users use that over the alternatives when dealing with HD video acceleration.

3) Not with accelerated drivers on both.  It's one or the other gets acceleration.

---

### Post by nickrout on 2012-04-29
> **superm1 said:**
> 1)

2) NVIDIA's VDPAU video acceleration is far more mature and stable at this point.  I would say a majority of MythTV Linux users use that over the alternatives when dealing with HD video acceleration.



nvidia has other useful options like loading an edid from disk (so it will start properly even with the TV turned off), overscan compensation etc. 

vdpau (the nvidia technology) will do deinterlacing as well as video decoding, vaapi will not do deinterlacing.

The maturity of the drivers is a major point.

If you have your PC doing all that, rethink things, get a small low power computer to plug into your TV as a frontend. Mythtv is meant to be an appliance, not an addon to a desktop.

---

### Post by odror on 2012-04-29
> **nickrout said:**
> nvidia has other useful options like loading an edid from disk (so it will start properly even with the TV turned off), overscan compensation etc. 

vdpau (the nvidia technology) will do deinterlacing as well as video decoding, vaapi will not do deinterlacing.

The maturity of the drivers is a major point.

If you have your PC doing all that, rethink things, get a small low power computer to plug into your TV as a frontend. Mythtv is meant to be an appliance, not an addon to a desktop.

I know all the good things that NVIDIA does, but I have 4 monitors. I would like to have gnome 3, not just kde. you are right that a small HTPC dedicated to mythtv is better. May be I will change it in the future. Until recently Linux was mostly my server. Now it is my main PC. I want to have the best user interface possible.

---

### Post by jyavenard on 2012-05-02
> **nickrout said:**
> 
vdpau (the nvidia technology) will do deinterlacing as well as video decoding, vaapi will not do deinterlacing.


It does do deinterlacing: Bob and Linear :)

But yeah, I totally agree. For a HTPC, and even for any PC going to run linux, nvidia is the way to go

---

### Post by nickrout on 2012-05-02
> **jyavenard said:**
> It does do deinterlacing: Bob and Linear :)


And temporal?

---

### Post by jyavenard on 2012-05-03
I would have listed it if it did :)

---

### Post by nickrout on 2012-05-03
The mythtv wiki says vdpau does temporal, is it wrong?

---

### Post by jyavenard on 2012-05-03
I thought this thread was about vaapi ?

VAAPI does do interlacing: linear and bob. That's it.

---

### Post by nickrout on 2012-05-03
> **jyavenard said:**
> I thought this thread was about vaapi ?

VAAPI does do interlacing: linear and bob. That's it.

I think we have both fallen foul of the ambiguity of the word "it"

I get your meaning now.

---

### Post by BicyclerBoy on 2012-05-04
@OP
nVidia has extended twinview to >2 screens in the latest drivers.
But separate X screens has real advantages especially for full screen video.
It allows easy full screen & independent video modes.

Xorg xinerama is deprecated & breaks openGL (& possibly vdpau overlay) on nVidia X server.

Not mythbuntu but..
Unity/compiz uses composite redirection & this is not guaranteed tear free.

There are setting (compiz ccsm) that limit the damage.
i.e. 'un-redirect full screen' is one. 
MythtV can work okay with Unity desktop & nVidia video cards.

I guess that is why avoiding compiz/composite effects on the HTPC is suggested.

---

### Post by odror on 2012-05-04
> **BicyclerBoy said:**
> @OP
nVidia has extended twinview to >2 screens in the latest drivers.
But separate X screens has real advantages especially for full screen video.
It allows easy full screen & independent video modes.

I have tried to use twinview > 2 screens ( i.e. 2 video cards) It did not work. My dirver is 295.40. Did you mean this driver?

can you use jockey to enable nvidia and ati cards on the same machine? If it is possible I'll use the nvidia card for my HDTV and the ati card for the desktop.

---

### Post by BicyclerBoy on 2012-05-04
twinview does not mean 2 video cards..
Not sure which driver version was stated in nVidia press release, starting to think it was 1st April release..
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NTY](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NTY)

[They have removed the simple GUI (interactive) overscan compensation slider & made it a xorg.conf viewport option..
It will be more flexible but so much harder to use.]

The X server runs on one GPU only. Some resource/load sharing is possible if the cards are similar or same (recommended) & the driver supports it.
But in this case the video outputs are still on primary card.

Unsubstantiated speculation follows disclaimer..
If the second card is different then I think it is possible it is driven as a simple frame buffer. USB display adapters work this way..
Don't know if twinview can include this type of screen..

I believe it would be possible to have both nVidia & AMD drivers loaded but you would to have to have only one openGL/GLX install.
Could be possible to run 2 independent X servers..

Or the optimus solution:
You could possibly use a modified Ironhide/Bumblebee script to switch between the 2 X drivers..
There are DIY video card docking stations using this method.

---

### Post by odror on 2012-05-05
> **BicyclerBoy said:**
> 
Not sure which driver version was stated in nVidia press release, starting to think it was 1st April release..
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NTY](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NTY)


This is exactly what I want, but it is not compatible with ubuntu 12.04. It needs a news X version.

In the meantime I installed the AMD 6850 card. It works great, except for mythtv. Forget acceleration. I do not get and good quality video playback. Multiple issues. I hope that I am doing something wrong. Any ideas how to set up mythtv correctly for this card. acceleration is not a big issue since I have a pretty capable core i7 CPU.

Thanks

---

### Post by nickrout on 2012-05-05
I think your question is answered earlier in the thread.

---

### Post by odror on 2012-05-05
> **nickrout said:**
> I think your question is answered earlier in the thread.
No exactly. The playback is horrible. In particular if I use video acceleration. I am not even taking about the interlace issue. I would like just to get it working. I am sure that I am doing something wrong.

---

### Post by nickrout on 2012-05-05
> **odror said:**
> No exactly. The playback is horrible. In particular if I use video acceleration. I am not even taking about the interlace issue. I would like just to get it working. I am sure that I am doing something wrong.

Well how about telling us about your playback settings! Are you using vaapi or not?

---

### Post by odror on 2012-05-05
> **nickrout said:**
> Well how about telling us about your playback settings! Are you using vaapi or not?
OS: ubuntu 12.04
video: HD6850
desktop: KDE
mythtv: 0.25

vainfo
>  vainfo
libva: VA-API version 0.32.0
Xlib:  extension "XFree86-DRI" missing on display ":0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               : VAEntrypointVLD
      VAProfileVC1Advanced            : VAEntrypointVLD


1. setup: VAAAPI Decoder VAAPI acceleration, render: openglvaapi OSD render: opengl2. (no deinterlacing) On playback I get vertically streached uninterlaced image.
2. Setup: high quality   decoder: standard  render: xv-blit OSD render: softblend deinterlacer: lnear blend. When playing I get non-smooth motion with extensive video tearing.
3. Setup: openGL high quality  decoder standard render: opengl OSD render: opengl deinterlacer: Greedy High Motion. I get jumping video (as if the CPU cannot keep up, although the cpu is far from max capacity. I also get video tearing.
4 Setup:norma  It is even worse (of #3) when I use the normal default setting

---

### Post by jyavenard on 2012-05-06
> **odror said:**
> 
1. setup: VAAAPI Decoder VAAPI acceleration, render: openglvaapi OSD render: opengl2. (no deinterlacing) On playback I get vertically streached uninterlaced image.


What did you expect? you don't do any deinterlacing, so of course it will be an uninterlaced image

> 
2. Setup: high quality   decoder: standard  render: xv-blit OSD render: softblend deinterlacer: lnear blend. When playing I get non-smooth motion with extensive video tearing.


If using ATI, enable the Tear Free Desktop , this gave me perfect playback.
but is rather CPU intensive for some reasons


> 
3. Setup: openGL high quality  decoder standard render: opengl OSD render: opengl deinterlacer: Greedy High Motion. I get jumping video (as if the CPU cannot keep up, although the cpu is far from max capacity. I also get video tearing.


You have pre-defined OpenGL profiles in myth, use them.
OpenGL Standard is almost as good as the "OpenGL High-Quality" one, but uses a fraction less CPU.
I find them virtually indistinguishable

---

### Post by jyavenard on 2012-05-06
I don't see much the point of using VAAPI to be honest.
Any intel processor supporting VAAPI is more than capable to do everything in software.

And you'll get better quality video (better deinterlacing) with the OpenGL playback profiles

---

### Post by odror on 2012-05-06
> **jyavenard said:**
> You have pre-defined OpenGL profiles in myth, use them.
OpenGL Standard is almost as good as the "OpenGL High-Quality" one, but uses a fraction less CPU.
I find them virtually indistinguishable
Thanks for your help. I  have setup "OpenGL Normal" It its better than anything else, but the motion is still not as smooth. I increased the number of CPU to 4. there was only minimal improvement improvement.

---

