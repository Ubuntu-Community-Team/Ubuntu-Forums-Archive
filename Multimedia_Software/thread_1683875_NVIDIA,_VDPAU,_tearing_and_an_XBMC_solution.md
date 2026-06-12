---
title: "NVIDIA, VDPAU, tearing and an XBMC solution?"
date: 2011-02-08
forum: Multimedia Software
---

### Post by rossmoore on 2011-02-08
Hi all,

I've been following and posting to various forums here, at nvidia, at compiz about the fact that on many nvidia systems video tears when shown with vdpau and with compiz (and thus composite) turned on. I know this is certainly true on my Atom + ION system. There are various posts about how to fix it by setting various things on Compiz, but the only one that I know reliably works on all Nvidia systems with VDPAU is turn composite completely off for the X session.

I've figured out a workaround that I use that launches a separate X session with composite switched off to watch videos - but it's clunky. That way though I can eye candy in my gnome session.

Yesterday I installed XBMC on my machine (as a normal program to run within my Gnome session), and discovered something wonderful. Somehow, the inbuilt DVDPlayer within XBMC is able to play back videos with VDPAU enabled, and without any tearing. I was gobsmacked.

What's going on? This indicates that it's clearly not a problem with X, with composite or with nvidia. So what is the problem, and why can't they fix it in mplayer or xine? What is XBMC's secret sauce for getting this working in XBMC? And is this final confirmation that the problem is with compiz (is  it turned off in some way within XBMC?)

---

### Post by beew on 2011-02-11
I use vdpau with Smplayer and XBMC with full Compoiz on my laptop. There used to be a bit of tearing with Smplaye, but I opened Compiz Settings Manager (You need to install it from the repo) ,  went to General Options > General and checked the box "Undirected Fullscreen Window" and the problem disappeared and video playback is really smooth.

As an aside, I notice that XBMC is actually not very good without vdpau. On my other machines (without Nvidia card) it performs very poorly comparing to both VLC and SMplayer. It struggles to play clips that the other players playback with ease and sometimes audio and video don't sync. But then it may be just my hardware.

BTW, I install Smplayer and mplayer from this ppa[URL="https://launchpad.net/%7Eripps818/+archive/coreavc"]
https://launchpad.net/~ripps818/+archive/coreavc[/URL]

It is a multithreaded version  of mplayer, works great with vdpau and also great without vdpau. I didn't bother with coreavc, don't have to install dshowserver if you don't want or need coreavc.

---

### Post by jwcalla on 2011-02-11
> **rossmoore said:**
> 
What's going on? This indicates that it's clearly not a problem with X, with composite or with nvidia. So what is the problem, and why can't they fix it in mplayer or xine? What is XBMC's secret sauce for getting this working in XBMC? And is this final confirmation that the problem is with compiz (is  it turned off in some way within XBMC?)

Is this when playing a video in XBMC in full-screen mode?  Is there any tearing when playing in windowed mode?

---

### Post by buster2209 on 2011-02-11
Go to; 

System -> Preferences -> CompizConfig Settings Manager -> General Options -> Display Settings

Texture Filter - Fast
Lighting - Checked
Detect Refresh Rate - Unchecked
Refresh Rate - SEE BELOW
Detect Outputs - UnChecked
Overlapping Output Handling - Smart
Outputs - SEE BELOW
Sync to VBlank - Checked

Your Refresh Rate and Outputs HAS TO be the same freq as your monitor.

E.g, I am 60hz and 1280x800 thus;

Refresh Rate - 60
Outputs - 1280x800+0+0

The best thing about this, it ONLY works if you have;

System -> Preferences -> Appereances -> Visual Effects

Select ANY setting except none.

This overwrites whatever you have set in NVIDIA X Server Settings.

I use this on my laptop with an NVidia 8400GS card and on a Revo 3700 (with NVIDIA ION) through SMPlayer and XBMC.

You can have choppy free and 'break line' free playback AND visual effects on!

---

### Post by b0b138 on 2011-02-12
> **buster2209 said:**
> Go to; 

System -> Preferences -> CompizConfig Settings Manager -> General Options -> Display Settings

Texture Filter - Fast
Lighting - Checked
Detect Refresh Rate - Unchecked
Refresh Rate - SEE BELOW
Detect Outputs - UnChecked
Overlapping Output Handling - Smart
Outputs - SEE BELOW
Sync to VBlank - Checked

Your Refresh Rate and Outputs HAS TO be the same freq as your monitor.

E.g, I am 60hz and 1280x800 thus;

Refresh Rate - 60
Outputs - 1280x800+0+0

The best thing about this, it ONLY works if you have;

System -> Preferences -> Appereances -> Visual Effects

Select ANY setting except none.

This overwrites whatever you have set in NVIDIA X Server Settings.

I use this on my laptop with an NVidia 8400GS card and on a Revo 3700 (with NVIDIA ION) through SMPlayer and XBMC.

You can have choppy free and 'break line' free playback AND visual effects on!

:guitar:  Tear free video!!!

This needs to be confirmed by more people and stickied or put on a gold plaque :KS

---

### Post by jwcalla on 2011-02-12
If you're using nvidia's twinview option you might need a little more love to get compiz to understand which display to sync to vblank.

Setting these OpenGL environment variables in my .xsession and .gnomerc to be executed before compiz started showed a massive improvement for me.

export __GL_SYNC_TO_VBLANK=1
export __GL_SYNC_DISPLAY_DEVICE=DFP-0

(where DFP-0 is the name of the display device to sync)

---

### Post by buster2209 on 2011-02-13
> **b0b138 said:**
> :guitar:  Tear free video!!!

This needs to be confirmed by more people and stickied or put on a gold plaque :KS

I concur.  I thought this only worked on my laptop but I just recently purchased a Revo 3700 (with an NVIDIA  Ion card) and the fix works on that too.

If it indeed works on other machines, maybe the 'tearing with NVidia card' problem can be finally laid to rest.

I know have personally wasted hours upon hours trying to solve this particular problem.....

---

### Post by rossmoore on 2011-02-13
Using mplayer or VLC with VDPAU and all those settings from buster2209 in compiz, I still get tearing in that area at the top of my screen on my ION Zotac board. Perhaps it's a bug in that - perhaps it just can't move data about fast enough for some reason.

No gold star and sticky from me, I'm afraid! Only thing that works for me is Boxee, or switching off composite. Maybe I'm alone in this battle, time for some new hardware.

---

### Post by buster2209 on 2011-02-13
> **rossmoore said:**
> Using mplayer or VLC with VDPAU and all those settings from buster2209 in compiz, I still get tearing in that area at the top of my screen on my ION Zotac board. Perhaps it's a bug in that - perhaps it just can't move data about fast enough for some reason.

No gold star and sticky from me, I'm afraid! Only thing that works for me is Boxee, or switching off composite. Maybe I'm alone in this battle, time for some new hardware.

Did you enable visual effects?

Also, ensure you have the right 'output' and freq.  They have to be **EXACT** otherwise you will get tearing.

BTW, how did you enable VDPAU in VLC?

---

### Post by rossmoore on 2011-02-17
I did enable visual effects, yes. Still tearing, full screen or in a window. It's minor, I'll grant you, but it's still there. My frequency is, of course not quite exact - the screen reports a fractional refresh frequency, while in compiz you can only specify an integer...

You can enable vdpau in vlc by installing the vdpau-va-driver - it's some kind of interface between vdpau and vaapi. With that installed, there are two hardware/GPU acceleration settings in the simple preferences dialogue of VLC - one in Video and one in Codecs. It certainly works, I can work 1080p on my box with minimal cpu usage (in vlc, mplayer or xbmc).

And I haven't tried boxee, sorry, I mistyped. It was xbmc (although of course they're based on the same code).

---

### Post by m042 on 2011-03-07
> **beew said:**
> I use vdpau with Smplayer and XBMC with full Compoiz on my laptop. There used to be a bit of tearing with Smplaye, but I opened Compiz Settings Manager (You need to install it from the repo) ,  went to General Options > General and checked the box &quot;Undirected Fullscreen Window&quot; and the problem disappeared and video playback is really smooth.

As an aside, I notice that XBMC is actually not very good without vdpau. On my other machines (without Nvidia card) it performs very poorly comparing to both VLC and SMplayer. It struggles to play clips that the other players playback with ease and sometimes audio and video don't sync. But then it may be just my hardware.

BTW, I install Smplayer and mplayer from this ppa[URL="https://launchpad.net/%7Eripps818/+archive/coreavc"]
https://launchpad.net/~ripps818/+archive/coreavc[/URL]

It is a multithreaded version  of mplayer, works great with vdpau and also great without vdpau. I didn't bother with coreavc, don't have to install dshowserver if you don't want or need coreavc.

I checked "Unredirect Fullscreen Window" as suggested here and my video tearing problems were gone! I wish I'd done this sooner. Using mplayer, no gui. Thanks!

---

### Post by gobbledigook on 2011-05-01
> **buster2209 said:**
> The best thing about this, it ONLY works if you have;

System -> Preferences -> Appereances -> Visual Effects

Select ANY setting except none.

This overwrites whatever you have set in NVIDIA X Server Settings.


just upgraded to natty... didn't like the default desktop so switched to classic (no effects) this post explains why i now have tearing :) i have now selected just classic....

thanx!

---

### Post by Dugger5688 on 2011-06-06
> **jwcalla said:**
> If you're using nvidia's twinview option you might need a little more love to get compiz to understand which display to sync to vblank.

Setting these OpenGL environment variables in my .xsession and .gnomerc to be executed before compiz started showed a massive improvement for me.

export __GL_SYNC_TO_VBLANK=1
export __GL_SYNC_DISPLAY_DEVICE=DFP-0

(where DFP-0 is the name of the display device to sync)

You are my hero! This needs to be stickied. I'm so sick of my vsync being set to my crappy acer 19" while my nice monitor tears all over the place.

---

### Post by allwise on 2011-08-02
> **buster2209 said:**
> Go to; 

System -> Preferences -> CompizConfig Settings Manager -> General Options -> Display Settings

Texture Filter - Fast
Lighting - Checked
Detect Refresh Rate - Unchecked
Refresh Rate - SEE BELOW
Detect Outputs - UnChecked
Overlapping Output Handling - Smart
Outputs - SEE BELOW
Sync to VBlank - Checked

Your Refresh Rate and Outputs HAS TO be the same freq as your monitor.

E.g, I am 60hz and 1280x800 thus;

Refresh Rate - 60
Outputs - 1280x800+0+0

The best thing about this, it ONLY works if you have;

System -> Preferences -> Appereances -> Visual Effects

Select ANY setting except none.

This overwrites whatever you have set in NVIDIA X Server Settings.

I use this on my laptop with an NVidia 8400GS card and on a Revo 3700 (with NVIDIA ION) through SMPlayer and XBMC.

You can have choppy free and 'break line' free playback AND visual effects on!

This or changing to Ubuntu Classic stopped the tearing in XBMC for xvid videos. mkv-files worked pretty good all the time, might have improved a bit now... 

I'm on a Asus AT330ION-Deluxe, passive cooling and ssd-drive.

---

### Post by chessplayer on 2011-08-12
> **m042 said:**
> I checked "Unredirect Fullscreen Window" as suggested here and my video tearing problems were gone! I wish I'd done this sooner. Using mplayer, no gui. Thanks!

Just wanted to let you know that in Natty the option has been moved from the "General" settings to the "Composite" settings in CompizConfig Settings Manager (CCSM). This notwithstanding, it still works! XBMC + tvheadend now give a perfect viewing experience!

So, all in all, just one little checkbox does the trick! Thumbs up!! :cool:

---

### Post by Jose Catre-Vandis on 2011-08-12
Slightly off topic but on Xubuntu 11.04 (with compositing enabled) I have a launcher in the "dock" that turns compositing on and off, making it easy to go tear free when needed. (There is a bug in Xubuntu that makes the dock disappear without compositing, so I need to run it most of the time) If I could be arsed I could write scripts and make launching the playing app (normally mplayer) turn off compositing before play and back on when finished, but my little launcher works just fine.

The code for doing it (in xubuntu) is:
OFF!
```
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=false
```
ON!
```
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=true
```

---

### Post by Danstroem on 2011-09-02
> **beew said:**
> There used to be a bit of tearing with Smplaye, but I opened Compiz Settings Manager (You need to install it from the repo) ,  went to General Options > General and checked the box "Undirected Fullscreen Window" and the problem disappeared and video playback is really smooth.


Thanks man, you saved my day :-) In combination with vSync enabled in Nvidia settings and in Compiz it's perfect! NVidia Corporation GT218 [NVS 2100M] (rev a2) with nvidia-current 280.13-0ubuntu1 on Maverick ([Ubuntu x-swat ppa]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")).

---

### Post by linux-warrior on 2012-01-14
> **chessplayer said:**
> Just wanted to let you know that in Natty the option has been moved from the "General" settings to the "Composite" settings in CompizConfig Settings Manager (CCSM). This notwithstanding, it still works! XBMC + tvheadend now give a perfect viewing experience!

So, all in all, just one little checkbox does the trick! Thumbs up!! :cool:

Just wanted to thank you! and confirm it works in Oniric too. I am on a Zotac zbox with Ion2. Tested with XBMC Eden Beta from the unstable ppa's:D

---

### Post by ewangr on 2012-04-15
Am hoping there might be some way to make these suggestions work on a non-XBMC solution that is attached to an LCD 42" screen?

I'm running 64-bit 12.04, and while I have installed VDPAU (at least the libraries that appear to be the right ones), am using the recommended nvidia driver (which doesn't seem quite as new as the other one in the restricted drivers dialog), and have installed the Compiz configuration tool as well as the latest VLC. With all that, I can't see where I can tell VLC to use VDPAU, the options in the Compiz tool don't seem to match what is described here, and it isn't clear which of the nvidia options I should be selecting.

System is an Atom 2 (i.e. a 64-bit dual-core Atom) with an ION-2 GPU and 3 gigs of RAM.

Suggestions?

---

### Post by jwcalla on 2012-04-15
> **ewangr said:**
> Am hoping there might be some way to make these suggestions work on a non-XBMC solution that is attached to an LCD 42" screen?

I'm running 64-bit 12.04, and while I have installed VDPAU (at least the libraries that appear to be the right ones), am using the recommended nvidia driver (which doesn't seem quite as new as the other one in the restricted drivers dialog), and have installed the Compiz configuration tool as well as the latest VLC. With all that, I can't see where I can tell VLC to use VDPAU, the options in the Compiz tool don't seem to match what is described here, and it isn't clear which of the nvidia options I should be selecting.

System is an Atom 2 (i.e. a 64-bit dual-core Atom) with an ION-2 GPU and 3 gigs of RAM.

Suggestions?

I'm not sure if VLC has good VDPAU support, but there should be an option somewhere to enable GPU-accelerated decoding.

[http://wiki.videolan.org/VLC_GPU_Decoding](http://wiki.videolan.org/VLC_GPU_Decoding)

---

### Post by BicyclerBoy on 2012-04-16
VLC can be made to use VAAPI. It does not have native VDPAU support.

There is a library package VDPAU backend for VAAPI (vdpau-va-driver)..
The performance/capability of VAAPI is a subset of VDPAU.
So you get better performance/PQ with mplayer.

---

### Post by ewangr on 2012-04-16
> **BicyclerBoy said:**
> So you get better performance/PQ with mplayer.

So just install mplayer and I should be good? Any preference between mplayer or smplayer or... ?

---

### Post by papibe on 2012-04-16
SMplayer is much easier to use than mplayer. SMplayer is a GUI app. [Here]("http://ubuntuforums.org/showpost.php?p=11760458&postcount=6") are a couple of tips to make it work with VDPAU.

Regards.

---

### Post by Shplad on 2012-05-23
Hi everyone:

EDIT: D'OH! SORRY - POSTED THIS BEFORE READING THE OP'S FIRST SOLUTION WAS SIMILAR.
MODS FEEL FREE TO DELETE-SORRY FOR ANY INCONVENIENCE

I tried the first couple of recommendations, and it seemed to really mess up my system. I can't remember what the effect was exactly. Not saying it doesn't work for others-just me.

I came across this idea over at XBMC.org forums

** [LINUX] Tearing on Nvidia?**
[http://forum.xbmc.org/showthread.php?tid=98108](http://forum.xbmc.org/showthread.php?tid=98108)

Before I commit any more screw-ups, has anyone tried this as a solution?
What were your results?
It seems really simple.

shplad

---

### Post by perevera on 2012-06-02
> **beew said:**
> I use vdpau with Smplayer and XBMC with full Compoiz on my laptop. There used to be a bit of tearing with Smplaye, but I opened Compiz Settings Manager (You need to install it from the repo) ,  went to General Options > General and checked the box "Undirected Fullscreen Window" and the problem disappeared and video playback is really smooth.

As an aside, I notice that XBMC is actually not very good without vdpau. On my other machines (without Nvidia card) it performs very poorly comparing to both VLC and SMplayer. It struggles to play clips that the other players playback with ease and sometimes audio and video don't sync. But then it may be just my hardware.

BTW, I install Smplayer and mplayer from this ppa[URL="https://launchpad.net/%7Eripps818/+archive/coreavc"]
https://launchpad.net/~ripps818/+archive/coreavc[/URL]

It is a multithreaded version  of mplayer, works great with vdpau and also great without vdpau. I didn't bother with coreavc, don't have to install dshowserver if you don't want or need coreavc.

I was experiencing this very same problem on my ASRock ION 330 with Ubuntu 12.04 and XBMC 2.11.

I then followed the instructions to check the box "Undirected Fullscreen Window" on Compiz Settings ("Composite" section) and it plays HD videos like a charm now.

Thanks so much.

---

### Post by perevera on 2012-06-05
> **perevera said:**
> I was experiencing this very same problem on my ASRock ION 330 with Ubuntu 12.04 and XBMC 2.11.

I then followed the instructions to check the box "Undirected Fullscreen Window" on Compiz Settings ("Composite" section) and it plays HD videos like a charm now.

Thanks so much.

Well, sorry, no, I am still having trouble to play HD videos (H264 with res. 1280x720).

Quality of image looks good with XBMC but there is a big problem with motion. At some points the action gets accelerated, then gets slower...

With SMPlayer I have a problem of audio and video tracks out of sync, even if I use options to synchronize them from Preferences.

In short, this is VLC (having installed vdpau-va-driver) what saves me as it plays these videos decently... a little bit of blurring on quick motions and sometimes pixelation, but ok.

---

