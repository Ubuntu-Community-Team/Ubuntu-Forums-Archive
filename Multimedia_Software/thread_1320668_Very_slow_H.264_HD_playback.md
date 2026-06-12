---
title: "Very slow H.264 HD playback"
date: 2009-11-09
forum: Multimedia Software
---

### Post by m1k3e on 2009-11-09
Hi all, first time posting here.  I've been a Red Hat user for a good 8 years who switched to Ubuntu a few years back, although I have to admit I'm really Mac user who loves toying with Linux ;-).  Anyways, I recently build a computer for the purpose of recording HD video and playing it back (I have a Hauppauge HD-PVR).  Anyways, I finally put the system together.  I'm able to record video from the HD-PVR just fine with "cat /dev/video0 > output.ts", but whenever I try to play the file back, it's very choppy and drops a LOT of frames.  This occurs when playing back with VLC, Totem, and mplayer.  I was able to achieve decent playback by compiling mplayer with ffmpeg-mt, but it's still running choppy.  I checked the output TS by playing the file back with EyeTV on my Mac and it played back flawlessly.  Any suggestions?  I'm running 9.10 x64.  My specs are AMD Phenom Quad @ 2.4 GHz w/ 4 GB of RAM and a built in ATI Radeon HD 3300.  I have the restricted ATI drivers enabled.  This system should be strong enough to playback HD full speed, I would think.  My Mac mini is only a 2.0 GHz CD w/ 2 GB ram and built-in video and it play the same file back flawlessly.  Again, any help would be appreciated. :)

Edit:  I probably should mention the file is a 720p60 MPEG-2 transport steam, H.264 @ 6.5 MBit/s with 128 KBit/s stereo AAC.

---

### Post by Lollerke on 2009-11-09
I think I have the same problem,check out my bug report.[HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478603[/HTML]
Do you have the same symptoms?

---

### Post by m1k3e on 2009-11-09
> **Lollerke said:**
> I think I have the same problem,check out my bug report.[HTML]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/478603[/HTML]
Do you have the same symptoms?

Seems just like it.  I restarted the computer in Windows 7 (:mad:) and it played back in WMP flawlessly.

---

### Post by bakhy on 2009-11-09
This happens to me as well, however it takes a while before it starts. My guess is that my graphic card is reducing speed due to overheating :S ATI Mobility Radeon HD 3470, BTW. I don't know much about these things, so I can't really estimate is this normal, or a sign of something not working right in the software, but all in all, it's a little disappointing. It happens 20-30 mins into a movie and effectively means I'm unable to watch HD movies. It would be nice if something could be done about it :/

I'll try cleaning the fans a little, and get back to you ;)

edit - Cleaning didn't help.

---

### Post by Cappientes on 2009-11-10
I've got the same issue. One of the comments on that bug reports suggests using xine (xine-ui in apt) and that certainly performs better and isn't as choppy. However it still prompts an error saying about too many dropped frames so something still isn't quite right.

---

### Post by Lollerke on 2009-11-10
Do you have an ATI card too? It looks like this is an ATI xorg-server issue .

---

### Post by Cappientes on 2009-11-10
Hi,

No I have a GeForce 9400 GT, running nvidia driver version 185.18.36, X version 11.0.

I am running 2 screens though, do you guys have this configuration?

C

---

### Post by Lollerke on 2009-11-10
I have one screen... It looks like a really weird bug.

---

### Post by xzero1 on 2009-11-10
I've have used the 3300IGP and the hdpvr. I have had no problems playing back my 720p .ts files at any bitrate using fglrx drivers or even with the standard radeon ones in 9.10 (although they are a bit more choppy). Currently, I use an external card and a UVD-2 hardware based XvBA driver and it is even better. 
See [http://www.phoronix.com/forums/showthread.php?t=19983]("http://www.phoronix.com/forums/showthread.php?t=19983")

The 3300IGP may support UVD-2 so you might want to try the method discussed in the forum. 

If not, the 3300IGP can still use accelerated texture rendering. If set up properly, there are no issues playing even 1080P@24 video.

See [http://ubuntuforums.org/showthread.php?t=1224509](http://ubuntuforums.org/showthread.php?t=1224509).

---

### Post by bakhy on 2009-11-11
Could it be that the only problem is that I had the "Unredirect fullscreen windows" option in CompizConfig turned off? It caused an annoying bug with Ubuntu 9.04, with the video disappearing when any other window wanted to be drawn over it (stuff like the volume control notification pop-up). As far as I can see the bug no longer exists, I turned the option back on and all that happens is a small flicker when VLC controls, or volume notifications pop up. With the option turned on I was able to watch an HD movie in VLC with no problems, although I've been unable to reproduce the buggy behaviour from yesterday with the option turned off... The only thing that's changed are some updates that I got today, one from the Telepathy PPA regarding FFmpeg, if I recall correctly. I didn't read the update description.

All in all, I'm completely lost, it's like the problem solved itself :/

Anyway, I guess I should keep the "Unredirect fullscreen windows" option on? What does that thing really do? Also, do I get anything from the tweaks described in the thread you linked to above, or is it best that I don't meddle now that everything seems to be working fine? I'm running Ubuntu 9.10, Catalyst 9.10, on an ATI Mobility Radeon HD 3470.

---

### Post by m1k3e on 2009-11-11
So I downloaded CompizConfig and enabled "Unredirect fullscreen windows".  HD video now plays full speed in VLC and mplayer-mt.  I still run into some artifacts during heavy motion but the frame rate is there.  Thanks for all the help! :D

---

### Post by Melcar on 2009-11-12
You guys need to keep in mind that ATI drivers (open or close) cannot fully accelerate HD material.  It's basically your CPU that will be doing most of the work.  1080p material is choppy even on a 3GHz Phenom, so I imagine it would be unbearable on a slower CPU.  ATI has given up on bringing UVD functionality to Linux (too much legal hassle), so they are planning to give us a replacement in XvBA; it's being worked on (beta users have access to the libraries) but who knows when it will be made available for end users.

---

### Post by xzero1 on 2009-11-12
> **Melcar said:**
> You guys need to keep in mind that ATI drivers (open or close) cannot fully accelerate HD material.  It's basically your CPU that will be doing most of the work.  1080p material is choppy even on a 3GHz Phenom, so I imagine it would be unbearable on a slower CPU.  ATI has given up on bringing UVD functionality to Linux (too much legal hassle), so they are planning to give us a replacement in XvBA; it's being worked on (beta users have access to the libraries) but who knows when it will be made available for end users.

Read my post in this thread. Its you can get it *now* and works well for some newer gpus!:D

---

### Post by xzero1 on 2009-11-12
> **bakhy said:**
> Could it be that the only problem is that I had the "Unredirect fullscreen windows" option in CompizConfig turned off? It caused an annoying bug with Ubuntu 9.04, with the video disappearing when any other window wanted to be drawn over it (stuff like the volume control notification pop-up). As far as I can see the bug no longer exists, I turned the option back on and all that happens is a small flicker when VLC controls, or volume notifications pop up. With the option turned on I was able to watch an HD movie in VLC with no problems, although I've been unable to reproduce the buggy behaviour from yesterday with the option turned off... The only thing that's changed are some updates that I got today, one from the Telepathy PPA regarding FFmpeg, if I recall correctly. I didn't read the update description.

All in all, I'm completely lost, it's like the problem solved itself :/

Anyway, I guess I should keep the "Unredirect fullscreen windows" option on? What does that thing really do? Also, do I get anything from the tweaks described in the thread you linked to above, or is it best that I don't meddle now that everything seems to be working fine? I'm running Ubuntu 9.10, Catalyst 9.10, on an ATI Mobility Radeon HD 3470.

In terms of video playback the most important option is textured video for AVIVO enabled cards See "Video Overlay on AVIVO cards on this link:

[http://wiki.cchtml.com/index.php/User_Contributed_Documentation#Video_Overlay_on_AVIVO_cards](http://wiki.cchtml.com/index.php/User_Contributed_Documentation#Video_Overlay_on_AVIVO_cards)

This gives partial video acceleration in Ubuntu as compared with full acceleration using UVD2.

---

### Post by bakhy on 2009-11-13
Thanks for the help!

I've read through my Xorg.log, and as I can see, TexturedVideo is enabled already. Also, the driver produces a line:
```
(II) fglrx(0): UVD2 feature is available
```
I guess that means he'll use it? I'm also guessing I should use XVideo as the output method in video playing programs?

P.S. As far as I've been able to digg out on the web, my card does not really support UVD2, only UVD+ :(

---

### Post by xzero1 on 2009-11-13
> **bakhy said:**
> Thanks for the help!

I've read through my Xorg.log, and as I can see, TexturedVideo is enabled already. Also, the driver produces a line:
```
(II) fglrx(0): UVD2 feature is available
```I guess that means he'll use it? I'm also guessing I should use XVideo as the output method in video playing programs?

P.S. As far as I've been able to digg out on the web, my card does not really support UVD2, only UVD+ :(

Check out the Phoronix link in my first post.  BTW, I would trust what fglrx reports rather than the web. The forum has a script to install a UVD2 enabled mplayer and required libraries. Note this is svn code and UVD2 only works with mplayer at this time.

---

