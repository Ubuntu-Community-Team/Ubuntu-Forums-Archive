---
title: "one (only) DVB-T channel has bad video quality"
date: 2010-09-27
forum: Mythbuntu
---

### Post by dibuntux on 2010-09-27
OK, this is very strange. I got one DVB-T channel (La7) that display bad video: strongly pixelated, image freezing, video loose sync with audio, on some scenes for a few seconds; than video is normal for a few seconds, and the process repeat again.
Video signal is fine at 72%; other channels display correctly with 65%. Other receiver (STB) on same antenna display the incriminated channel correctly.
What is VERY strange, is that ads display correctly: I got problem ONLY during regular transmission, whatever they are (news, movies, sport, ecc.). And no, the channel is FTA.


Any idea? TIA

Mythbuntu 10.04 AMD64
Gigabyte GA-M720
Athlon X2 4800+
Nvidia 9400GT 1GB
WD Sata2 CaviarGreen
Skystar 2 DVB-s
Nova T-500 dual DVB-T
Denon AVR 1610 connected with SPDIF
Optoma HD700x on DVI

---

### Post by ian dobson on 2010-09-27
Hi,

Can you try recording something from the bad channel, then try playing it back with vlc or mplayer (not the MythTV frontend video player) just to see if it's a problem with the signal or the playback.

It could well be that during the adverts that have a different encoding rate/video format and the frontend software just can't handle it that well.

Regards
Ian Dobson

---

### Post by dibuntux on 2010-09-27
Exactly what I thought, Ian. I tried to watch the tv channel from my remote machine:
Ubuntu 10.04 AMD64 with latest frontend as Myth BE
Athlon X2 64 7750 4GB DDR2 800
SVGA ATI HD2400Pro

MythTV playback profile: Slim (so everything is done by the CPU)

I've the frontend on this machine windowed at the same res of my main FE/BE mythbox, 1280x720, connected at 100Mbs. It plays correct! Even maximizing the window to full screen, 1680x1050, the video is perfect, ads and shows.

On my machine I use MythTV playback profile:VDPAU Normal

So, it is something related to NVIDIA driver &/or VDPAU?

Still I have to try playing it back... I'll let you know ASAP.

Thanks

---

### Post by ian dobson on 2010-09-27
Hi,

vdpau is part of the NVidia driver. VDPAU is hardware aceleration for videos on linux. I've seen on my frontend that when the video as errors (no matter how small) the video playback breaks up abit.

Maybe try playing with the vdpau options (high quality,performance etc).

regards
Ian Dobson

---

### Post by dibuntux on 2010-09-28
I tried with the recording, same thing. If I change profile to Slim instead of VDPAU Normal the channel displays fine (albeit with some reception errors). The problem is that after using VDPAU you cannot go back: standard TV res on my 3mt diagonal screen is just unwatchable without VDPAU.

I just have to add this channel to my collection of other files I cannot play with Myth (some .mkv that play fine using Boxee).

Maybe in the next release of the Nvidia driver...

Thanks for your helping

---

### Post by ian dobson on 2010-09-28
Hi,

I think the 256.x version of the NVidia driver improves the playback of dodgy videos abit when using VDPAU.

I think mythbuntu has 196.x as standard at the moment.

Came across this:-
```
nVidia released the new 256.35 display drivers as stable, just 2 days after the release candidate.

nVidia 256.53 graphics drivers highlights:

Added unofficial GLX protocol support
Improved Thermal Settings reporting in nvidia-settings to accurately reflect hardware configurations with multiple thermal sensors.
Fixed an interaction problem between Compiz and ‘screen-scraping’ VNC servers like x11vnc and vino that caused the screen to stop updating.
Enhanced VDPAU to add basic support for Xinerama. VDPAU will now operate on a single physical X screen under Xinerama. See the README for more details.
Enhanced VDPAU’s handling of corrupt clips of all formats on GPUs with VDPAU feature set C to be at least as good as on GPUs with VDPAU feature set B. This significantly improves various clips provided by nvnews.net user eamiller.
Fixed a bug in Xv attribute handling that caused hue, saturation,brightness, and contrast values to be misapplied when using an Xv overlay adaptor.
Implemented new APIs to allow sharing VDPAU surfaces with OpenGL andCUDA.
Removed precompiled kernel interfaces from the NVIDIA Linux-x86 .run file;
```

Regards
Ian Dobson

---

### Post by LowSky on 2010-09-28
You can get Nvidia's 260 driver by using the PPA.

VDPAU is much improved over the older 196 driver, and all newer card are supported like the GTX 4xx series.

---

### Post by kokkonenfi on 2010-09-29
Try adding some custom filters, check the Mythtv wiki or my web site for that 
[http://kokkonen.fi/vdpaucustomfilters](http://kokkonen.fi/vdpaucustomfilters)

for me this works: 
vdpauskipchroma,vdpaucolorspace=auto,vdpaubuffersize=32

---

### Post by dibuntux on 2010-09-29
Hei kokkonenfi, this one worked! Thanks a lot for your input!

I just created a custom VDPAU profile based on Normal with your custom filters added. It even solved the problems I had with my .mkv files!

Hope it can be of help to others.

All my best to all!

---

### Post by kokkonenfi on 2010-10-11
Nice to hear it works for you too.

---

