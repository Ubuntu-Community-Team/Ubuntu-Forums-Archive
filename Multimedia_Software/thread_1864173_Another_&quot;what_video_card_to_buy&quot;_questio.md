---
title: "Another &quot;what video card to buy&quot; question"
date: 2011-10-18
forum: Multimedia Software
---

### Post by BudworthTDog on 2011-10-18
Sorry to post ANOTHER “what kind of graphics card should I get” question but I couldn't really find anything specific to my situation and use.  
 

 First of all here is what I have

Ubuntu 11.10 64-bit
AMD Phenom II X4 955
8GB RAM

Screen 40" Samsung 60hz 1080p hooked up HDMI

Current Video Card
GeForce 210
CUDA Cores 16
Memory 1024MB 
Memory Interface 64bit
Bus Type PCIe x16 Gen2
Driver Version 280.13

The main thing I use my desktop is to watch Movies and TV shows. I view them as AVI and MVK files in VLC. When I run Unity in 3D mode the videos are glitchy. Kind of jumpy and horizontal lines making the picture uneven flowing up and down the screen. When I run it in 2D mode it is much better. When I watch HD cable TV I realize my computer could run a smother flowing picture. I'm not terribly picky but I haven't put any money into my computer lately so I was thinking of treating myself. 

I know I want a nvidia card but spec wise what kind of card should I get in order to get very good to excellent HD video and if it doesn't break the bank run Unity 3D as well.

---

### Post by BicyclerBoy on 2011-10-18
GT430 is best HTPC card at the moment.

The GT210 is a dog..

A GT530 or 540 would be great if they were not OEM only..

VLC uses the CPU decode unless you get/build a version with VA-API.
You can get a VA-API for VDPAU library..

Unity 3d/compiz can interfere with video playback including VDPAU.
There is tweaking required.

You should look at XBMC or MythTV.

All the latest gen nVidia video card have VDPAU decode.
So you could buy a GT560ti or 580 & have fast openGL & good video.

---

### Post by wolfen69 on 2011-10-18
> **BicyclerBoy said:**
> GT430 is best HTPC card at the moment.



I have the same card, and it works great in 11.10. Plus it's pretty cheap now.

---

### Post by BudworthTDog on 2011-10-18
> **BicyclerBoy said:**
> GT430 is best HTPC card at the moment.


VLC uses the CPU decode unless you get/build a version with VA-API.
You can get a VA-API for VDPAU library..



As far as the GT430 goes how do you think this one looks?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814127541](http://www.newegg.com/Product/Product.aspx?Item=N82E16814127541)

Out of all the 5 star reviews it's the cheapest. Not the best way to shop I know but I'm Jewish so I cant help it. 

I'm not sure what all you're getting at with the CPU decode, VA-API, VDPAU business. I'm going to start to look into what all that means and the pros and cons tomorrow as its past my bedtime. You don't have to explain it all as I'm sure there are plenty of threads on it already but if you could let me know if I just have the basics of this down than it will help let me know what exactly to read into.

My interpretation is that VLC by default uses the CPU to decode the picture unless you use VA-API which uses the GPU to decode. 

Now as far as VDPAU I'm not sure what that means other then Unity/Compiz can effect it.

In all honesty I'm not a terribly picky guy when it comes to the picture. I want a good "HD" picture but before long you kind of hit a point where the differences are minuscule in relation to how much tweaking of settings you do and money you put into it. As I said before I'm watching AVI and (mostly) MKV files so that alone makes for a ceiling in graphics unlike the ever changing gaming world.

So do you think I would get a significant improvment with the GT430 without jacking around tweeking settings all over the place? I have used XBMC and MYTHTV but I prefer the basic'ness (not a word I know) of VLC.

---

### Post by BicyclerBoy on 2011-10-19
You got the idea pretty much right..

Stuff is so cheap in the US makes my eyes water..

VLC does have a nice clean un-blinged aesthetic..

VDPAU is an open std api designed by nVidia for video decode etc in GPU h/w.
Any GPU manufacturer could choice to use it..there was a rumour that intel were considering..

VA-API is (open source) incomplete but supported on AMD (XvBA), nVidia (VDPAU) & intel GPUs.

MythTV & XBMC & mplayer support VDPAU directly.

You have enough CPU power to decode any strange material.

Unity 3d use compiz composite manager (blitter) & requires some openGL peformance.
The GT430 is about 3.5x faster than GT210. 
They both have the same video bitstream processor but..
The GT430 can run the video post-processing where the GT210 can not.

The tweaks to unity/compiz for good video playback in VDPAU & VLC are not 
 difficult (11.04).

---

### Post by BudworthTDog on 2011-10-22
> **BicyclerBoy said:**
> 

The tweaks to unity/compiz for good video playback in VDPAU & VLC are not 
 difficult (11.04).

The graphics card I posted up last reply came in yesterday and I installed it. Things do come in much better but still just a few little hiccups here and there, nothing like before and honestly quite tolerable, I think I'm just watching to hard for them. 

In any case how would I go about these tweaks you were talking about? I am running 11.10.

---

### Post by BicyclerBoy on 2011-10-22
I guess you you using ubuntu 11.10 with unity/compiz.
The symptom of composite affecting video is the appearance of a horizontal tear line 1/5 down screen on panning video & an anoying stutter every ~5 seconds. (AV resync).

With 11.04 unity to get perfect full screen video in VDPAU required a couple tweaks in ccsm compiz composite settings manager.
composite tab, tick un-redirection of full screen
workarounds tab, tick legacy full screen support

The last one is for MythTV full screen (& possibly others).

Did not expt with VLC (no VAAPI)..I guess you need sync vertical blank set for XVideo & openGL (both in nvidia-settings).
May need to try the different video overlay methods to find the best.
VLC needs yadifx2 filter for any interlaced material. You may have CPU issues with x2.

---

### Post by BudworthTDog on 2011-10-24
Thank you for all your help. I have notice a significant improvement! Is it still possible to mark a thread SOLVED? I looked into it but only found answers from '09 that said it had been disabled. Is this still true?

---

### Post by BicyclerBoy on 2011-10-24
Don't know about the solved thread button, it never happens...

You should try VDPAU with Myth or mplayer & try the different settings..
In MythTV you would use HQ VDPAU profile.

VAAPI probably can not config VDPAU the same way.

You don't get so much lift for VLC...but check you are not using X11 video.

---

### Post by jmate24 on 2011-10-24
get the ati raedon 5670 it is HD and it works well with any *ubuntu.
[http://http://www.newegg.com/Product/Product.aspx?Item=N82E16814102917]("http://http://www.newegg.com/Product/Product.aspx?Item=N82E16814102917")

---

### Post by BicyclerBoy on 2011-10-24
Thanks for correcting my nVidia bias..

How's XvBA working with VA-API ?
HDA over HDMI ?
VA de-interlacing/hq scaling control ?

AMD's multi-monitor support does take top prize tho..
Twinview & (> 2) screens on nVidia is a joke.. 
Composite/compiz problems still plague nVidia X server..

---

