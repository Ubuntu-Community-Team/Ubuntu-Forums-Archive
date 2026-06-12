---
title: "Smooth video playback difficulty with SIS/nVidia cards"
date: 2012-04-21
forum: Multimedia Software
---

### Post by framo on 2012-04-21
Hi, I am running 11.10 (Ubuntu) on an older PC (hp/compaq presario sr1010z - AMD64) with 2GB RAM.
It came with a built-in SIS video card (128 MB memory).
So to reduce stress on the main system, I installed a nVidia card with [[COLOR=blue][/COLOR]]("http://www.linuxforums.org/forum/#") 512 MB mem.  
 
But no matter which one I use, depending on the site or video type, if I go fullscreen, the video is very choppy.
 
Output from lspci shows the two as follows
   [COLOR=#000000][COLOR=#0000BB][/COLOR][/COLOR] lspci | grep VGA
00:09.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

 
 I have gone through  System Settings > Additional Drivers and installed the recommended  version for the newer (nVidia) card but to no avail.
 
Any recommendations on improving the video quality?
 
While I am an experienced app developer on Unix/Linux, don't know much about tweaking the system[]("http://www.linuxforums.org/forum/#") from a sysadmin perspective.
 
Will disabling one free up resources overall?
 
Are there updates needed that I am unaware of?
 
Thanks much!

---

### Post by BicyclerBoy on 2012-04-21
Modern video compression is very CPU/GPU intensive.

There is no video h/w decode acceleration until some nVidia 8000 chipset graphics & the discrete 8400 up..
(there is partial decode support in earlier models)

You can get nVidia 8500GT PCI (VDPAU feature set A)..
There was rumour that maybe the 8400 was available as AGP 

Probably the best player (performance) is mplayer..might take some cmd line option tweaking to get the best..

What are the video specs?
Install/Use 'mediainfo' to provide a metric..

You could try a non-unity desktop like gnome-fallback or Xfce etc..
Unity is very hard on old video cards & interferes with video performance especially with nVidia.

If using unity or compiz..run ccsm & set "un-redirect full screeen".

---

### Post by framo on 2012-04-22
Thanks for the response, I am in fact running the gnome desktop (not Unity) and also have Xfce and Xubuntu which are lighter.   But the problem is even with YouTube video streaming from a website.  

Oddly, a locally stored video file is mostly okay, but the live streaming ones from most websites are horribly choppy (when in full screen mode) and there is a significant delay in response to keystrokes.  

For example, once in full screen, if I hit the escape key to return to normal size, it takes a good 5-10 seconds to come back and then the video suddenly fast forwards to catch up with the audio.

---

### Post by BicyclerBoy on 2012-04-22
The streamed video will be H264 in some quicktime or flash format..

Can you try a local video file in similar format. I do not suggest downloading a sample..

Getting video acceration working in the browser is a problem in Linux unless it is WebM &/or works natively or with open source plugins.
Have a look at flashreplace or "lovinglinux"'s tutorial on flash plugins..

Going to get worse (or better) now Adobe has stopped linux support.
With Youtube you can opt-in for webM video stream instead of the dreadful flash player..but not all media is avail in webM yet.

---

### Post by SeijiSensei on 2012-04-22
NVIDIA cards before the 8xxx series don't support VDPAU so they provide little help in decoding H.264 material.  I had a P4 with a GeForce 64xx and couldn't play 720p H.264 material smoothly at all.  I had to re-encode those video files to use XviD on that platform.

My current machine has a 9500GT, and I can use VDPAU if needed.  However this machine's CPU is fast enough that I don't really need it.

The current version of flashplayer is supposed to take advantage of VDPAU-capable NVIDIA cards, but the player has a bug that transposes the colors.  People's faces turn blue if hardware acceleration is enabled!  NVIDIA is apparently working on a fix for the problem since Adobe has stopped supporting flashplayer on Linux.

---

### Post by framo on 2012-04-22
Locally save video files work fine in mplayer, vlc, etc.  Attached is the 'mediainfo -f' output on that file
I even tried a locally save high quality video (I think HD) mp4 file and that worked great.

Ironically, the live streaming on my Dell Inspiron 1501 (AMD 64 x2 Turion) is great, or any video from anywhere.

---

### Post by BicyclerBoy on 2012-04-22
That video file is flash H264 but low res & low bitrate (about 10x lower than dvb-t broadcast HD)
An atom netbook should play this..

---

