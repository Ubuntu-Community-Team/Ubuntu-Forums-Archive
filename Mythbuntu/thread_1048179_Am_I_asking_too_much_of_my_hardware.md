---
title: "Am I asking too much of my hardware?"
date: 2009-01-23
forum: Mythbuntu
---

### Post by nicoloks on 2009-01-23
Just installed MythBuntu 8.10 using the Nvidia 180.22 drivers and ALSA 1.0.19 on my system with the following specs;

AMD X2 3800+
2 x 512MB DDRII400
Onboard Geforce 6150 SE 256MB shared ram
Onboard MCP61/ALC888 7.1 HD audio

I've found it all works very well, with one exception. I get bad video and audio stutter when view full HD content, although watching live or recorded full HDTV (MPEG2) is fine. [According to Nvidia]("http://www.nvidia.com/page/purevideo.html") the Geforce 6150 SE should support hardware based HD video acceleration for H.264, WMV/VC-1 & MPEG4, however when watching HD content in these formats CPU usage is pegged at 100% yet when watching HDTV it doesn't get about 50%.

So my questions are;

1) Using the Nvidia X Server settings manager I can see that direct rendering is enabled. Is there anything else I need to check, install or configure to ensure that all my hardware based video acceleration is being utilised?

2) As my motherboard does not have SPDIF out I am currently using the analog outputs for surround sound, which I assume means that the sound processing is being done by the CPU. Does anyone know if this overhead is significant? Better yet, does anyone know how I can temporarily disable and re-enable my soundcard totally so I can test this?

3) What other things can I do in Mythbuntu to increase the performance for HD content? For instance, if I move the MythTV backend to another machine will this free up significant resources that are likely to result in a noticable increase in performance?

Any other tips or jems of advice apart from upgrading my hardware would be greatly appreciated!

---

### Post by ian dobson on 2009-01-23
Hi,

Your CPU might be abit slow for HD TV. Under linux the hardware acceleration for HD video on NVidia is known as vdpau and is still quite new.

There are patches in MythTV version 0.22 for vdpau but they're quite new and abit buggy.

Have a look here [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU)
Regards
Ian Dobson

---

### Post by jMon54 on 2009-01-23
Also check your recording profiles.  For me CPU-- works best.  And of course your Xorg.conf file has to be configured to take advantage of the nVidia's capabilities. You can do a search for that.  Good luck.

---

### Post by newlinux on 2009-01-23
By full HD content are you talking h.264 1080p? What is the codec/format of the files it is struggling with? What content is it that you are playing and where does it come from?

That CPU/GPU combo is plenty fast for Mpeg-2 HD content (which is what most signals in mythtv record as). I have that GPU and that processor. You shouldn't even need any hardware acceleration. That card will only support XvMC mpeg-2 acceleration  as VDPAU is only supported on 8 series and higher cards.

My X2 3800 with a nvidia 6200 can playback mpeg-2 HD with no problems, and  720p h.264 with no problem, and I don't use hardware acceleration. My X2 4200 with the onboard 6150 can as well... Both, however, would struggle with 1080i/p h.264 playback.

1. Make sure you have
```
Option	   "UseEvents" "on"
```
in the video card Device section(s) of your /etc/X11/xorg.conf

2. Let us know what playback profile you are using. You might want to try different ones, or create your own.

3. Are you using the internal player or mplayer (or something else) to play back the non mythtv recordings you are having problems with? If you are not using the internal player you can ignore the playback profile stuff as your problem

---

### Post by jMon54 on 2009-01-23
Here's a snippet from my xorg.conf.  Note: I had to use XvMC in order to enjoy HD which I get over-the-air and watch on a Samsung 42" TV at 720p.

<snippet>
Section "Device"
	Identifier     "Configured Video Device"
	Option "UseEvents" "true"
	Option "XvmcUsesTextures" "false" # necessary for color Chromakey OSD
	Option "NVAGP" "3" # some users report 2 or 3 works better
	Option "DPI" "100x100"
	Driver	"nvidia"
EndSection
</snippet>

---

### Post by sloggerkhan on 2009-01-23
there are 2 parts of rendering HD:
decode and the actual redering.
With mpeg-2, the decode isn't as cpu intensive as VC-1 or h264.
To decode well encoded 1080P streams in h264 or VC-1, you need about 2.5+ ghz dual core to guarantee CPU decode and playback (as usually the bottleneck is in the decode.)
If you add the patched for nvidia's new decode API, you should be able to get 1080P playback fine. Otherwise you should reencode at 720P or with mpeg2 instead of h264.

---

