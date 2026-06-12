---
title: "Video tearing, Intel i3 graphics"
date: 2011-08-28
forum: Multimedia Software
---

### Post by Jethoss on 2011-08-28
I have a dedicated HTPC running Natty (Ubuntu classic, no effects)  that's mainly used as a  MythTV box.  I'm getting a lot of tearing in the video approximately 1/3 of the way down from the top of the screen.

Hardware:
Intel Core i3 560 (Clarkdale)
Gigabyte H55M-USB3 motherboard
HVR-2250 TV card

I'm using the onboard graphics with an HDMI cable to a receiver, then on to an LCD TV. Neither the receiver nor the TV does any added video processing.  I had been getting a lot of stuttering during playback, but switching to classic, no effects fixed that and replaced it with the tearing problem.

I've looked and looked, but haven't had any luck finding a solution to this.  I LOVE the system, but the video is really getting frustrating.

Thanks for any ideas you can provide.

---

### Post by BicyclerBoy on 2011-08-29
The best performance intel drivers come from xorg-edgers launchpad ppa.
You have to use all their packages not just pick one.

There is a tweaking tool for DRI2
driconf
check the vsync settings..
Post 
glxinfo | grep OpenGL

The real performance boost would come from using VA-API.
The driver supports mpeg2 & H264 decoding.

---

### Post by Jethoss on 2011-08-29
Thanks for the info, I'll definitely try that.  The output from glxinfo is:

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Desktop GEM 20100330 DEVELOPMENT 
OpenGL version string: 2.1 Mesa 7.10.2
OpenGL shading language version string: 1.20
OpenGL extensions:

---

### Post by BicyclerBoy on 2011-08-30
FYI
11.04 & using xorg-edgers launchpad ppa on 945GME results in:

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 945GME x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.12-devel

You should look into VA-API

---

### Post by Jethoss on 2011-08-31
Ok, I think I got VA-API updated through xorg-edgers, and got all the packages.  glxinfo now reads:

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Desktop 
OpenGL version string: 2.1 Mesa 7.12-devel
OpenGL shading language version string: 1.20
OpenGL extensions:

The problem I'm having now is that Myth crashes if I try to use OpenGL.  I'm guessing that I just missed a driver somewhere along the way.  Any idea what to look for next?

---

### Post by BicyclerBoy on 2011-08-31
does this crash ?
glxgears 

driconf

Could be a regression..hope for an update. seem to come every other day.

---

### Post by Jethoss on 2011-09-02
glxgears seems to run without incident, and reports very close to 60 fps.  I worked my way through the driconf settings with no luck there, either.  If I use OpenGL in MythTV, it crashes.  Everything else seems to work, just with the tearing problem.

I might just be stuck waiting for updated drivers...

---

### Post by drawkcab on 2011-09-02
I've noticed that minor tearing happens after a kernel update.  If I reinstall ffmpeg again after a kernel update, the tearing goes away for hd video.  I've never been able to reinstall the right drivers to improve tearing on standard def .avi files, but playing them back in xbmc resolves the tearing.

On another note, vlc, which is my preferred .avi player, is just a mess right now.  It is sluggish to start, audio and video are out of sync, audio problems require a restart after pausing...etc.  VLC has always been rock solid for me except in the last few weeks.

---

