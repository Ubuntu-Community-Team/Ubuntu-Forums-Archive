---
title: "Latest nvidia driver update = poor vdpau performance"
date: 2011-10-16
forum: Multimedia Software
---

### Post by thecapsaicinkid on 2011-10-16
10.04 LTS
Nvidia G210 gpu

EDIT: To save people reading through this thread, the solution was to upgrade to a later mplayer (see last post)


After downgrading from 11.04 to 10.04 LTS, playing HD h264 encoded videos with VDPAU results in massive A/V desync.


mplayer -vo vdpau -vc ffh264vdpau -demuxer lavf myvid.mpg


Output is similar to; (printed repeatedly)

```
pts value < previousV: 1.944
```

---

### Post by Blackkitten on 2011-10-17
Same problem. It seems that after 256.XX drivers vdpau perfomance is broken.

Here is a [thread on nvnews]("http://www.nvnews.net/vbulletin/showthread.php?t=155618"). It is one year old but there is still nothing. 

I've had this problem when updated to 11.04. Now on 11.10 the problem is still here. Any useful information would be appreciated. 
And please write about your problem at nvnews.

---

### Post by BicyclerBoy on 2011-10-17
nVidia 260 VDPAU on 10.04.3 LTS working fine for months..actually VDPAU has been working very well for last 3+ years.

11.04 with std repos nvidia driver version & VDPAU works okay only if you configure compiz/composite.
11.10 has the same problem (compiz).

This sounds more like mplayer/ffmpeg/libav bug..

---

### Post by Blackkitten on 2011-10-17
> **BicyclerBoy said:**
> nVidia 260 VDPAU on 10.04.3 LTS working fine for months..actually VDPAU has been working very well for last 3+ years.

11.04 with std repos nvidia driver version & VDPAU works okay only if you configure compiz/composite.
11.10 has the same problem (compiz).

This sounds more like mplayer/ffmpeg/libav bug..

What problem with compiz are you talking about?
On 11.04 I tried to start session without compiz ("ubuntu without effects" or smth like this in the login screen) and the problem was still here.
Can you provide some links?

P.S. I know about working vdpau on 10.04. But in newer realeses and with newer drivers it seems that vdpau becomes slow.

Also check the the thread on nvnews. Maybe you'll notice something that we didn't. But for now it doesn't looks like mplayer/ffmpeg/libav bug.

And thanks for a reply!

---

### Post by thecapsaicinkid on 2011-10-17
New versions of Ubuntu, VDPAU performance was good. I've just downgraded to 10.04 LTS and am having big problems (namely BBC HD recordings) There was the odd issue before the latest update but after the update last week, all unplayable.

I'm guessing version of binary nvidia driver is the same regardless of Ubuntu version?

Is an older, working version of the driver available in the repo to revert back to?

---

### Post by BicyclerBoy on 2011-10-17
BBC HD is likely high bitrate.
The GT210 is so slow (shaders) that you can't run the feature set C or 2x advanced DI (VA de-interlace).

You may be able to get a bit more out the GT210 by looking into the settings used by ION (vdpaubuffers).
Keep lowering the DI settings 2xhw --> 1xhw-->bob etc..

You can not get rid of compiz from 11.04 or 11.10 without removing/replacing the desktop manager i.e. xubuntu xfce.

The setting in ccsm/composite that causes vdpau slowdown is: unredirect fullscreen (not ticked/selected).
You may need legacy full screen selected.
Check the sections composite, openGL & workarounds.

There are/were many 3rd party ppa for nvidia drivers:
xorg-edgers, x-swat team, nvidia team etc 
I think 10.04 is not so well supported now.
I have never used the Ubuntu repos for nVidia driver on HTPC but see no reason it should not be okay.

---

### Post by thecapsaicinkid on 2011-10-17
> **BicyclerBoy said:**
> BBC HD is likely high bitrate.
The GT210 is so slow (shaders) that you can't run the feature set C or 2x advanced DI (VA de-interlace).

You may be able to get a bit more out the GT210 by looking into the settings used by ION (vdpaubuffers).
Keep lowering the DI settings 2xhw --> 1xhw-->bob etc..

You can not get rid of compiz from 11.04 or 11.10 without removing/replacing the desktop manager i.e. xubuntu xfce.

The setting in ccsm/composite that causes vdpau slowdown is: unredirect fullscreen (not ticked/selected).
You may need legacy full screen selected.
Check the sections composite, openGL & workarounds.
I've been playing Blu-ray/BBC HD flawlessly until now.

---

### Post by BicyclerBoy on 2011-10-17
Version 260.19.xx is working fine with 10.04.3 lts.
I don't have compiz/composite active..

Compiz was working okay with VDPAU last time I checked (4 months ago?)

Do you have any desktop effects enabled ?
Try turning them off ?

There is a truck load of VDPAU settings that mplayer could be hiding/pre-selecting/ignoring

---

### Post by thecapsaicinkid on 2011-10-17
```
qvdpautest 0.5.1
Intel(R) Core(TM)2 Duo CPU     E7300  @ 2.66GHz
NVIDIA GPU GeForce 210 (GT218) at PCI:2:0:0 (GPU-0)

VDPAU API version : 1
VDPAU implementation : NVIDIA VDPAU Driver Shared Library  195.36.24  Thu Apr 22 10:39:56 PDT 2010

SURFACE GET BITS: 1016.05 M/s
SURFACE PUT BITS: 620.327 M/s

MPEG DECODING (1920x1080): 67 frames/s
MPEG DECODING (1280x720): 162 frames/s
H264 DECODING (1920x1080): 61 frames/s
H264 DECODING (1280x720): 132 frames/s
VC1 DECODING (1440x1080): 78 frames/s
MPEG4 DECODING (1920x1080): 72 frames/s

MIXER WEAVE (1920x1080): 303 frames/s
MIXER BOB (1920x1080): 507 fields/s
MIXER TEMPORAL (1920x1080): 142 fields/s
MIXER TEMPORAL + IVTC (1920x1080): 93 fields/s
MIXER TEMPORAL + SKIP_CHROMA (1920x1080): 187 fields/s
MIXER TEMPORAL_SPATIAL (1920x1080): 60 fields/s
MIXER TEMPORAL_SPATIAL + IVTC (1920x1080): 47 fields/s
MIXER TEMPORAL_SPATIAL + SKIP_CHROMA (1920x1080): 68 fields/s
MIXER TEMPORAL_SPATIAL (720x576 video to 1920x1080 display): 210 fields/s
MIXER TEMPORAL_SPATIAL + HQSCALING (720x576 video to 1920x1080 display): 127 fields/s

MULTITHREADED MPEG DECODING (1920x1080): 62 frames/s
MULTITHREADED MIXER TEMPORAL (1920x1080): 93 fields/s
```

This is a clean install with compix disabled, X is running the display at 1080p50.

---

### Post by Cavsfan on 2011-10-17
I am running 280.13 (the latest nVidia driver) with 10.04 64 bit. And everything works great.

[[COLOR=blue]_Get the latest nVidia driver here._[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

[[COLOR=blue]_Instructions on how to install nVida driver._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") - not for the meek but, it works well.

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

The last one is a tutorial from this forum.

I also use compiz and everything on a 1920x1200 monitor.

I have a Geforce 9800GT.

---

### Post by Cavsfan on 2011-10-17
This method does not update. You have to manually check for updated drivers if desired.

---

### Post by BicyclerBoy on 2011-10-17
There are lots of comments about that test tool..
It is not a true measure & its tests are a very specific use-case.

The GT210 temporal-spatial (2xadv h/w or VA DI) is borderline for 60Hz, in reality the GT210 is too slow for 50Hz.

Check your powermiser settings...Try setting to max & replay the problem HD recording.

You can get later drivers pre-compiled in ppa..
Building the nVidia way is not difficult just annoying.
Just read the nVidia driver readme (documentation 2nd to none).

Maybe need to find out the mplayer settings for vdpau & see if this has changed.
Most users would want all features (C or D) enabled.

---

### Post by Blackkitten on 2011-10-18
> **thecapsaicinkid said:**
> I've been playing Blu-ray/BBC HD flawlessly until now.

Same for me. I tried to check powermizer for maximum perfomance, runnning session without effects (in 11.04) but still nothing.

Before the problem appeard I could play 1080p videos and blurays with effects disabled. And 720p videos in any case.

P.S. And in 10.04 everything was working "out of the box" without manual install of drivers, clean fresh install etc.

P.P.S. Some of you guys using poewrful GPUs compared to mine (8600m GT - the one that was using in notebooks). This also matters. As even with speed perfomance issues you will be still getting good results. But not me. Because this bug drops my GPU decoding abilities below comfort zone.

---

### Post by BicyclerBoy on 2011-10-18
I have a MythTV demo box (i3) using old 9400GT ..so as slow as the GT210..
It is running 11.04 Unity/compiz..
I think you can not get rid of unity/compiz without changing to Xubuntu Xfce (mythbuntu).

This PC works as well as expected (VDPAU video).

Do you have cssm/composite un-redirect full screen selected/ticked ?
This stops compiz (blitter) from wrecking full screen VDPAU overlay.

---

### Post by Blackkitten on 2011-10-19
> **BicyclerBoy said:**
> ...
Do you have cssm/composite un-redirect full screen selected/ticked ?
This stops compiz (blitter) from wrecking full screen VDPAU overlay.

So, I started from your advice about "un-redirect full screen".
I didn't have it ticked. When I selected it the vdpau perfomance became smooth ( tested on video from Nikon D7000 that is 1080p@24fps ). Then I stared to measure perfomance with qvdpau testing tool... In the end I dicovered next things:

**1.** It looks like that "un-redirect full screen" option doesn't affect perfomance.

**2.** Vdpau perfomance is switching from smooth to bad without any noticable causes. Usually it is smooth after restart or changing the session, but after some time it becomes too slow.
Usually Unity2d session has smoother results, than Unity 3d, but in general they are on par. I have next qvdpautest results:

Unity2d session. Smooth VDPAU.
```
qvdpautest 0.5.1
Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)

VDPAU API version : 1
VDPAU implementation : NVIDIA VDPAU Driver Shared Library  285.05.09  Fri Sep 23 17:55:14 PDT 2011

SURFACE GET BITS: 821.865 M/s
SURFACE PUT BITS: 737.28 M/s

MPEG DECODING (1920x1080): 57 frames/s
MPEG DECODING (1280x720): 124 frames/s
H264 DECODING (1920x1080): 25 frames/s
H264 DECODING (1280x720): 57 frames/s
VC1 DECODING (1440x1080): 72 frames/s

MIXER WEAVE (1920x1080): 531 frames/s
MIXER BOB (1920x1080): 894 fields/s
MIXER TEMPORAL (1920x1080): 204 fields/s
MIXER TEMPORAL + IVTC (1920x1080): 135 fields/s
MIXER TEMPORAL + SKIP_CHROMA (1920x1080): 277 fields/s
MIXER TEMPORAL_SPATIAL (1920x1080): 70 fields/s
MIXER TEMPORAL_SPATIAL + IVTC (1920x1080): 58 fields/s
MIXER TEMPORAL_SPATIAL + SKIP_CHROMA (1920x1080): 78 fields/s
MIXER TEMPORAL_SPATIAL (720x576 video to 1920x1080 display): 270 fields/s

MULTITHREADED MPEG DECODING (1920x1080): 60 frames/s
MULTITHREADED MIXER TEMPORAL (1920x1080): 172 fields/s

```

Unity3d session. Smooth vdpau.
```
qvdpautest 0.5.1
Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)

VDPAU API version : 1
VDPAU implementation : NVIDIA VDPAU Driver Shared Library  285.05.09  Fri Sep 23 17:55:14 PDT 2011

SURFACE GET BITS: 812.373 M/s
SURFACE PUT BITS: 684.472 M/s

MPEG DECODING (1920x1080): 57 frames/s
MPEG DECODING (1280x720): 123 frames/s
H264 DECODING (1920x1080): 24 frames/s
H264 DECODING (1280x720): 53 frames/s
VC1 DECODING (1440x1080): 72 frames/s

MIXER WEAVE (1920x1080): 529 frames/s
MIXER BOB (1920x1080): 672 fields/s
MIXER TEMPORAL (1920x1080): 152 fields/s
MIXER TEMPORAL + IVTC (1920x1080): 99 fields/s
MIXER TEMPORAL + SKIP_CHROMA (1920x1080): 208 fields/s
MIXER TEMPORAL_SPATIAL (1920x1080): 54 fields/s
MIXER TEMPORAL_SPATIAL + IVTC (1920x1080): 44 fields/s
MIXER TEMPORAL_SPATIAL + SKIP_CHROMA (1920x1080): 63 fields/s
MIXER TEMPORAL_SPATIAL (720x576 video to 1920x1080 display): 202 fields/s

MULTITHREADED MPEG DECODING (1920x1080): 61 frames/s
MULTITHREADED MIXER TEMPORAL (1920x1080): 171 fields/s
```

Unity3d session. Bad vdpau perfomance.
```
qvdpautest 0.5.1
Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)

VDPAU API version : 1
VDPAU implementation : NVIDIA VDPAU Driver Shared Library  285.05.09  Fri Sep 23 17:55:14 PDT 2011

SURFACE GET BITS: 816.466 M/s
SURFACE PUT BITS: 630.061 M/s

MPEG DECODING (1920x1080): 34 frames/s
MPEG DECODING (1280x720): 74 frames/s
H264 DECODING (1920x1080): 15 frames/s
H264 DECODING (1280x720): 33 frames/s
VC1 DECODING (1440x1080): 42 frames/s

MIXER WEAVE (1920x1080): 523 frames/s
MIXER BOB (1920x1080): 671 fields/s
MIXER TEMPORAL (1920x1080): 151 fields/s
MIXER TEMPORAL + IVTC (1920x1080): 98 fields/s
MIXER TEMPORAL + SKIP_CHROMA (1920x1080): 207 fields/s
MIXER TEMPORAL_SPATIAL (1920x1080): 54 fields/s
MIXER TEMPORAL_SPATIAL + IVTC (1920x1080): 43 fields/s
MIXER TEMPORAL_SPATIAL + SKIP_CHROMA (1920x1080): 63 fields/s
MIXER TEMPORAL_SPATIAL (720x576 video to 1920x1080 display): 202 fields/s

MULTITHREADED MPEG DECODING (1920x1080): 38 frames/s
MULTITHREADED MIXER TEMPORAL (1920x1080): 174 fields/s
```

**3.** The funny thing.
The results above was take using notebook's display: 1280x800.
Switching to external display(1920x1080) gives better vdpau perfomance!
```
qvdpautest 0.5.1
Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
NVIDIA GPU GeForce 8600M GT (G84) at PCI:1:0:0 (GPU-0)

VDPAU API version : 1
VDPAU implementation : NVIDIA VDPAU Driver Shared Library  285.05.09  Fri Sep 23 17:55:14 PDT 2011

SURFACE GET BITS: 825.82 M/s
SURFACE PUT BITS: 742.96 M/s

MPEG DECODING (1920x1080): 71 frames/s
MPEG DECODING (1280x720): 143 frames/s
H264 DECODING (1920x1080): 41 frames/s
H264 DECODING (1280x720): 86 frames/s
VC1 DECODING (1440x1080): 105 frames/s

MIXER WEAVE (1920x1080): 492 frames/s
MIXER BOB (1920x1080): 836 fields/s
MIXER TEMPORAL (1920x1080): 193 fields/s
MIXER TEMPORAL + IVTC (1920x1080): 129 fields/s
MIXER TEMPORAL + SKIP_CHROMA (1920x1080): 262 fields/s
MIXER TEMPORAL_SPATIAL (1920x1080): 68 fields/s
MIXER TEMPORAL_SPATIAL + IVTC (1920x1080): 56 fields/s
MIXER TEMPORAL_SPATIAL + SKIP_CHROMA (1920x1080): 76 fields/s
MIXER TEMPORAL_SPATIAL (720x576 video to 1920x1080 display): 263 fields/s

MULTITHREADED MPEG DECODING (1920x1080): 67 frames/s
MULTITHREADED MIXER TEMPORAL (1920x1080): 161 fields/s
```

P.S. I'm using mplayer from [this PPA]("https://launchpad.net/~ripps818/+archive/coreavc").
And nvidia-drivers from [this PPA]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=oneiric").

---

### Post by BicyclerBoy on 2011-10-19
That's very good result..
It clearly shows that:
- video decode VDPAU is slowing down.
- openGL load from unity3d c.f 2d
- good & bad vdpau playback have the same openGL benchmark

The results clearly show there is more opengl load with unity3d than 2d (54 - 70 field/s 2xadv-DI).

The decoding benchmark should not be effected by any openGL performance changes because decode runs in the VPU bitstream processor.
The MIXER temporal spatial is the 2xadv de-interlacing that runs in the shader engine.

Maybe your ccsm settings are being over written by some startup default..
Are you using twinview ?

VDPAU is meant to work with twinview..
Your video card has good openGL performance, is it not slow, faster than GT210 & 9400GT.
The video decode bitstream processor VPU has much the same throughput on all video cards except the GT520.

Decoding always happens at native resolution & then is scaled in shaders to display size. Later video card do the scaling better (feature set C & D).

---

### Post by Blackkitten on 2011-10-19
After my "tests" and your reply everything is clear for me now ( improving perfomance by switching to larger display, little differences between unity2&3D sessions ) except that slow down in VDPAU perfomance !

I tried to figure out the situation when it happens but no luck here. 
I don't know how the slowdown depends from time and from my actions. Will try this later again because I couldn't find any dependancy for now . But surely after sometime or after some actions the perfomance becomes bad.

I don't use twinview. I just switch the displays by changing xorg.conf and restrating the session (is there a better way ?).

---

### Post by BicyclerBoy on 2011-10-19
I don't understand the VDPAU slowdown either...

My demo box MythTV 9400GT version 270.xx  VDPAU behaves okay with compiz un-redirection.

The guaranteed way to maximise OGL VDPAU performance is
editing /etc/X11/xorg.conf to kill composite.

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

This old thread is good reading about composite problems with nVidia.
[http://phoronix.com/forums/showthread.php?25362-Gaming-Benchmarks-Windows-7-vs.-Ubuntu-Linux/page3](http://phoronix.com/forums/showthread.php?25362-Gaming-Benchmarks-Windows-7-vs.-Ubuntu-Linux/page3)

There may be no option but to use a non-compositing desktop Xubuntu Xfce, that's what mythbuntu is built on...

Ubuntu 10.04 LTS (compiz off) is looking better by the minute...that's what I use on the the main HTPC box..


There are some good ideas here:
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)
I was not aware of the AMD CPU/bus clock scaling or the intel power management issues..

---

### Post by BicyclerBoy on 2011-10-20
Expted with qvdpautest on the ubuntu 11.04 unity (running classic gnome2).
nvidia 270 9400GT.

VDPAU performance was much as expected from 9400GT.
Decode H264 1080 45 frames/sec (okay)
Mixer temporal-spatial 1080 55 fields. (too slow)

qvdpautest does not seem to be affected by any of the compiz/composite settings.
qydpautest does not seem to be affected by disabling composite in xorg.conf.

But:
qvdpautest does not use full screen.
This VDPAU benchmark does not reflect real world use (using MythTV).


Is your laptop GPU using system RAM ?

vdpaubuffers = 32 (or higher)
Option "TripleBuffer"  "True"

---

### Post by Blackkitten on 2011-10-21
How to check if my laptop's GPU is using system RAM? 
My GPU has 512Mb of it's own memory. I doubt it needs more for usual tasks.

I tried to use " Option "TripleBuffer" "True" " in xorg.conf but this didn't eliminate vdpau slowdown.

And about " vdpaubuffers = 32 (or higher) " - How to check what I'm using? I don't set it to any value. Maybe I'm using default?

As I said before I'm using mplayer with smplayer. I just select vdpau in options and that's all.

P.S. I think now that vdpau slowdown depends more on time. So smth ruins my vdpau perfomance.
Also I discovered that after waking up from "wait mode" ( the one that requires energy to be active ) vdpau perfomance restores.

---

### Post by BicyclerBoy on 2011-10-21
I have no experience with mplayer..it is likely there is some obscure cmd line options for VDPAU.

vdpaubuffers seems to be a hack for ION users & I think MythTV dynamically configures it. I would think mplayer does something similar.

Maybe you have the CPU clock/bus scaling slowdown ?
This webpage mentions CPU clock scaling (near bottom) 
[http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)

---

### Post by thecapsaicinkid on 2011-10-21
I've just noticed, mplayer output is also full of
```

[h264_vdpau @ 0x7609900]number of reference frames exceeds max (probably corrupt input), discarding one

```

I've also tested a series of other HD sample videos (Bluray rips + high bitrate 1080p 50fps) and they all play back silky smooth. It looks like there are issues with the videos MythTV is creating or the version of mplayer I have.

---

### Post by BicyclerBoy on 2011-10-21
MythTV does not interfere/transcode recordings from digital tuners.

It configures the pid filters & streams the tuner card output to a file (mpeg2-ts)

MythTV internal player works better than mplayer (subjective) except for BD.
MythTV can play BD but not from menu option yet..

Try MythTV internal player on the mpeg2-ts recordings (.mpg).

---

### Post by thecapsaicinkid on 2011-10-22
Just tried the internal player, same result, slow video plus the sound breaks up.

I guess my 2 options are, upgrade the nvidia driver (which I don't really want to do) or go back to the latest Ubuntu.

The reason I switched back to LTS was for stability reasons, plus I had a weird issue where all video playback would have a small band of offset pixels.

---

### Post by BicyclerBoy on 2011-10-22
I have been using nvidia 260 on 10.04 for many months with GT240

You can get package managed drivers from 
xorg-edgers ppa
x-swat team ppa 
jya's mythtv ppa.
maybe from mythbuntu ?

---

### Post by thecapsaicinkid on 2011-10-22
Thanks. I think I'll add the x-swat ppa and grab the latest driver.

So, how does the driver stay in sync with my kernel version, what happens with kernel updates that are pushed out to 10.04?

Also, I'm going to want to set a priority for the PPA so I only get the nvidia driver and not the other stuff. Will google that.

---

### Post by thecapsaicinkid on 2011-10-22
So I've tried;

[LIST]
[*]Upgrading to latest nvidia driver v285.05.09 via PPA
[*]Playback in MythTV player instead of mplayer (all VDPAU profiles low/normal/high)
[*]Disabling compositing and enabling triple buffering in xorg.conf
[*]Setting gpu+cpu scaling to max performance
[/LIST]


Nothing works.

So, these HD DVB-S(2) recordings are interlaced right? If bluray rips and other progressive HD/high bitrate videos play back fine, then the problem lies with deinterlacing?

Even if I set MythTV plaback to use the low end deinterlacing, it makes no difference.

---

### Post by thecapsaicinkid on 2011-10-22
Sussed it!

It's Pulseaudio (*spit*) causing it. Went back to Alsa and everything is roses.

---

### Post by thecapsaicinkid on 2011-10-22
Well, half solved it. 

For these particular videos, mplayer won't play smoothly regardless of audio output, even set to null and it's still jerky. Mythfrontend plays the same video fine when alsa is set (mythtv must suspend pulse with 'pasuspender' in the background) but laggy when pulseaudio is set as output.


Confused.

---

### Post by BicyclerBoy on 2011-10-22
The packaged video drivers from ppa have installer scripts etc.
The installer scripts handle dependencies & compiling against kernel version.
The module is inserted using dkms & boot image is recreated.

If you choice to use xorg-edgers then note that you should use all their packages.

My main MythTV HTPC uses alsa directly to support digital pass-thru'.
Music playback is via custom alsa device to hq up/resample to maximum supported by HT amp.

The demo myth box was using pulseaudio okay ..but it has the time scheduling/interrupt scheduling configuration change to fix AV sync in VLC.


There must be a VDPAU setup difference between mplayer & mythtv.
Remember your video card can not do (adv x2) deinterlace. (VDPAU high Q in mythtv)

Your qvdpautest benchmark suggests card can:
- not do MIXER temporal spatial HD 1080  (2x adv de-interlacing)
- do HQ scaling okay
- not do inverse telecine at HD 60 fields/sec.
I have only found one DVD that needed inverse telecining & that was SD..
(Pink Floyd The Wall PAL DVD)

other features.
Your card has feature set C but the test does not reveal denoise/sharpen performance.
Some of these features must interact & accumulate to overload the shaders.

---

### Post by thecapsaicinkid on 2011-10-22
I'm not trying to use temporal spatial, never have done. The performance of the card isn't the issue, I've played these videos fine pre-downgrade and they play fine in Mythfrontend with pulseaudio disabled. Mplayer defaults to no deinterlacing but changing it makes no difference anyway(deint=0/1/2/3/4)

This isn't a long term solution as I rely on pulse to downmix 5.1 to 4.1 (I have no centre) not to mention using alsa with myth blocks the soundcard.

I need to find a way to get apps to output to pulse without killing my video performance.

---

### Post by BicyclerBoy on 2011-10-22
IMO Broadcast OTA TV & DVD are unwatchable without a good de-interlacer.

BD are different because they can be low frame rate progressive.

You can downmix in alsa.
If you are just outputting discrete analogue audio then you can share in alsa..(not offering to help)

Why does audio sharing matter with MythTV frontend ? It is a full screen interface kind of program.

I don't have a need to use pulse audio because it does not allow (does with latest version) digital pass-thru', no AC3 encoder for multi-channel audio (non AC3/DTS). The alsa re-sampler matches/betters pulse resampler.

You could try to find a recent build 10.04 ppa for mplayer..the 4th ppa link posted earlier has one..

---

### Post by thecapsaicinkid on 2011-10-23
> **BicyclerBoy said:**
> IMO Broadcast OTA TV & DVD are unwatchable without a good de-interlacer.
Temporal spatial for SD and Temporal for HD, hardly unwatchable!

I like to have Spotify running to swith to which afaik only supports pulse output.

Will try a later mplayer.

---

### Post by thecapsaicinkid on 2011-10-23
Upgraded mplayer using daily ppa and it now works fine.

```
sudo add-apt-repository ppa:motumedia/mplayer-daily

sudo apt-get update && sudo apt-get install mplayer
```

I'll stick to using Mythweb to play recordings using mplayer and not bother with Mythfrontend. 

Playback is smooth in mplayer for 1440x1080 h.264 recordings using Temporal DI and high-qualityscaling

```
vo=vdpau:deint=3,hqscaling
```


**So in summary;**

Default mythfrontend shipped with 10.04 performs poorly with vdpau with pulseaudio output on my hardware.

Default mplayer shipped with 10.04 performs poorly with vdpau regardless of audio output on my hardware.

---

### Post by BicyclerBoy on 2011-10-23
I would think you would be hard pressed to find anyone using the ubuntu repos versions of mplayer or mythtv.
Even more so for ubuntu 10.04.

Sorry I did not even consider that you were..

The majority of MythTV users are quite conservative but get myth from mythbuntu or jya ppa or build from source.

mplayer users are more cutting edge than myth users..

---

### Post by thecapsaicinkid on 2011-10-23
I've been an Ubuntu user for almost 7 years and nearly the same for MythTV and always ran bleeding edge code, compiled from source sometimes. I got fed up of various little bugs/playback niggles. Even if I resolved them new ones would be replaced with updates. 

Now I thought I'd go back to the LTS to see if I could get a more stable system without the irritations. Hopefully 10.04 with a few choice upgrades and only applying important security updates will provide this.

---

### Post by Blackkitten on 2011-10-29
I'm not 100% sure but I think it's POWERMIZER causing vdpau perfomance degradation on my system.

I've noticed that if set powermizer to max.perf. right after restart/boot/waking up from sleep mode then vdpau perfomance is always good and it doesn't degrade as I've reported earlier.

But if I set/leave it on adaptive then it goes to "0" mode perfomance when there is nothing to do for the GPU and vdpau perfomance also goes down no matter what you do after (even setting poewrmizer to max.perf doesn't help).

Only thing that helps is to restart the system or make it sleep and make it wake up or to log out and log in.

---

### Post by thecapsaicinkid on 2011-10-30
I'm going to have to give up on 10.04, I've resolved a few issues but VDPAU is still problematic and I'm convinced it's related to the audio stack.


MythTV (standard version) plays back HD recordings with VDPAU 'Normal'/Alsa but with a slight (constant) audio desync.

mplayer (ppa version) plays back HD recordings with VDPAU (deint > 1)/Pulse but at set points in the video will suddenly start dropping frames like crazy and doesn't recover until you seek. The points/severity of the framedrop is dependant on what audio track you select. SD videos also seem affected and will eventually crash mplayer

---

