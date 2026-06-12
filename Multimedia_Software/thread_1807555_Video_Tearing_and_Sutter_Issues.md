---
title: "Video Tearing and Sutter Issues"
date: 2011-07-19
forum: Multimedia Software
---

### Post by Qbert on 2011-07-19
I have a HTPC running Natty.  I have some experience with Linux, but still consider myself new.  My HTPC has an AMD 45w quad core and a nVidia 520 GPU with 2GB of memory.  The PC side of it works fine, but I am having issues with video playback, mainly some tearing and stutter issues.  

I have a bunch of DVD and Blu-ray rips.  The DVDs were coded with Handbrake while the Blu-rays were done with RipBot.  All were done using the same settings.  I have no stutter issues with the DVDs, but they can tear, though not as often as the Blu-rays.  The stutter issue only happens with a few videos.  The video stops while the sound continues while the video catches up.

So far I've tried disabling compiz, but that hasn't helped much.  I wonder if there's some codec or other piece I'm missing?  I have the latest nVidia drivers installed.  I've been using VLC, but did notice the same issues in the native movie player.  If I toss Windows on the machine and use Media Player Classic, the videos play just fine.  Can anyone lend some assistance?  Thanks for any help.

---

### Post by BicyclerBoy on 2011-07-19
What ubuntu release ?
What video driver version ?

The GT520 is relatively new & is not supported by the 10.04 nvidia-current (about May 2011).
You need nvidia version 270 or later..

You should understand that VLC & totem do not use nvidia video hardware decode (VDPAU/PureVideo).
Your windows setup likely includes "filters" that utilize h/w decode.

Your linux playback is likely using single threaded CPU playback so slow.

XBMC & MythTV & mplayer (variants.. smplayer etc) support VDPAU directly.
VLC can support VA-API..there is a backend VDPAU for VA-API library in the mix...

Later builds of these support multi-threaded execution.

---

### Post by Qbert on 2011-07-20
Thanks BicyclerBoy.  I'm using 11.04 x64 with the latest updates.  The driver version is 270.41.06.

What do I need to do get it to work right?  If I wait for a better driver will that fix it?  Mplayer had the same issues.  I used to have a 210m card, but it didn't have sound via HDMI, which I need.  That's why I went with the 520.  Thanks again.

---

### Post by BicyclerBoy on 2011-07-20
You have to get your VLC/mplayer/smplayer from some 3rd party ppa.
The std ubuntu repos will not likely solve your problems..

Search these forums for smplayer..various people were touting it ..

I am surprised your CPU decode playback is so bad..a core2duo has no problem.
Could be due to quad core & single thread app.
CPU decode does put more demand on RAM & the PCIe bus.

To re-iterate:
VLC can use VA-API but to use this you need to install VAAPI & the VDPAU backend for VA-API.
(s)mplayer/XBMC/MythTV can drive VDPAU directly.

Note that the GT520 is about as slow as GT210 except is has VDPAU feature set D & is fermi based.
If you use VDPAU it will be okay.
Both GT210 & 520 suffer the same problem in that the shaders performance does not allow VA de-interlacing filters & hq scaling (DVD playback etc)
The GT430 GT530 (oem) are recommended HTPC.

---

