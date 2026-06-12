---
title: "no 'vdpau-video' for Meerkat AMD64 ?"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by bsmith1051 on 2010-09-08
I've got a test box running the beta of 10.10 64-bit with the specific goal of gaining hw accelerated h.264 playback.  (All my home videos for the past 2 years are AVCHD.)  I'm using an Nvidia 8400 and the current 256.53 Nvidia-proprietary driver.

I've read that hw-acceleration requires updated ffmpeg which only 10.10 has, but I'm still not getting accel from the latest VLC 1.1.4.  Yes, I have the option for HW Accel enabled!

I believe the problem is that there is no sign of the 'vdpau-video' in Synaptic.  I found it listed in Launchpad for i386 but not for x64
[https://launchpad.net/ubuntu/+source/vdpau-video/0.6.3-1/+build/1794285](https://launchpad.net/ubuntu/+source/vdpau-video/0.6.3-1/+build/1794285)

Am I correct in my troubleshooting?  If so, when will all the 'parts' be available for AMD64 ?

P.S. I also tried adding the Nvidia 'Cutting Edge Multimedia' PPA but they don't have Maverick Meerkat support at all yet, much less AMD64.

---

### Post by VeeDubb on 2010-09-08
On my system, vdpau works just fine.  (10.10 64bit)

Latest nvidia drivers and libvdpau.

It might be libvdpau0 or libvdpau-1, but eithe way, it's libvdpau.

Ah, I see.  It's not that vdpau isn't functioning, it's just that it's not functioning in the media apps you need it for.  The only media player I use where vdpau is really an issue, is Boxee.

---

### Post by mc4man on 2010-09-08
I believe you're correct, though the vlc build on maverick doesn't seem to have a dep on vdpau-video - left for one to install manually

On a 32 bit install (8400) I can enable gpu accel, but it will fail if vdpau-video isn't installed (fails to find /usr/lib.dri/nvidia_drv_video.so which links to vdpau_drv_video.so

With it installed then
> libva: va_openDriver() returns 0
[0xb6726f94] avcodec decoder: Using VA API version 0.31 for hardware decoding.


You could maybe try getting vdpau-video from splitted-desktops - it has a debian folder inside and will build easily to a normal debian package


Overall on the 8400 I find for H.264 that mplayer w/vdpau blows vlc and vaapi away
I consider my 8400 to be marginal at best - ( laptop 8400)

Edit; I was using my own built 1.2 vlc, so removed the packages, installed 1.1.4 from repo and see the same thing - with vdpau-video installed it's fine as above, with it removed see this
> libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns -1
[0x99917ec] avcodec decoder warning: Failed to open VA API

---

### Post by bsmith1051 on 2010-09-08
Thanks for the replies!  I spent a lot of time trying to make mplayer work but it was less than optimal.  If I used the command-line I could get it to launch full-screen and with beautiful playback of my AVCHD (including deinterlacing), but then I had no GUI.  If I used smplayer I couldn't get the playback to work the same, even when I manually coded the same command-line options.

So I'll stick with VLC for now.

Maybe when there's another update to mplayer and/or smplayer I'll try that again.

---

### Post by mc4man on 2010-09-08
I would wait and see if there is a vdpau-video release for amd64 if it needs it..?
Run vlc from cli with -vvv and look for above mentioned error

Took a look at the splitted source  - it installs by default to /usr/lib/va/drivers so there would be some work to use
(knew there was a reason I went with repo libs this time for maverick

Otherwise maybe file a bug against if it doesn't shape up

Edit:
considering vdpau-va-driver has been in debian for some time ...
> Yes, I have the option for HW Accel enabled!
You do mean the option in 'Inputs and Codecs' - "Use GPU acceleration"

---

