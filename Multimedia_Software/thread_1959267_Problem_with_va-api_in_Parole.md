---
title: "Problem with va-api in Parole"
date: 2012-04-15
forum: Multimedia Software
---

### Post by raptir on 2012-04-15
I'm currently running Xubuntu 64-bit on an HP DM1 (Core i3 2367m with Intel HD 3000 integrated graphics). Out of the box, 720p H264 video played fine with Parole, but I was getting very high CPU usage. I installed gstreamer0.10-vaapi at the recommendation of a post I read to try to get hardware acceleration working to pull down the CPU usage during playback. But with that package installed I get the following terminal output when trying to play a video in Parole:

```
Stream with high frequencies VQ coding
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns -1

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstffmpeg.so
```

Are there any other packages I need to get hardware acceleration for video playback (h264 specifically) working? I haven't been able to find a decent guide for doing so on Intel graphics, so if you can even just link a guide I'd appreciate it. Thanks, and let me know if there's any additional info I can provide.

---

### Post by BicyclerBoy on 2012-04-15
The intel driver has native vaapi support..so IFAIK need the following as a minimum:
libva
i965-va-driver
libva-glx1

you can check the library setup with:
vainfo

You might have more success using xorg-edgers xorg launchpad ppa..
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
This will update your xorg/mesa/intel driver/libva etc..

This thread has interesting history:
[http://forum.xbmc.org/showthread.php?tid=86581](http://forum.xbmc.org/showthread.php?tid=86581)

---

### Post by raptir on 2012-04-15
So, after installing i965-va-driver (the others were installed) I get the following return from vainfo:

```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.15
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD

```

When trying to play in Parole now, I get: 

```
libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
Stream with high frequencies VQ coding
** Message: don't know how to handle video/x-surface, width=(int)1920, height=(int)1080, framerate=(fraction)2500000/104271, pixel-aspect-ratio=(fraction)1/1, type=(string)vaapi, opengl=(boolean)true

```

Parole no longer crashes, but the video still does not play. Do I need to go through and compile mplayer with vaapi support, or are there any binaries available that support vaapi properly? Or am I missing something else? Thanks.

---

### Post by Yellow Pasque on 2012-04-16
I never got the gstreamer-vaapi output working, though I was using ATI/AMD cards and the vaapi/xvba wrapper.

VLC is a good video player that support va-api without building your own version.

---

### Post by raptir on 2012-04-16
Alright, I tried VLC. With GPU decoding unchecked, I get similar results to Parole without the vaapi package installed, as expected. With GPU decoding checked, I'm actually getting much worse performance. I see about the same CPU usage, but the video stutters constantly. VLC doesn't seem to have any useful terminal output, so if you can let me know what logs VLC generates I can provide those.

I can run the same file in Windows with MPC-HC and DXVA with no issues, so I know that the GPU is powerful enough.

Thanks again for any help.

---

### Post by BicyclerBoy on 2012-04-16
You have not stated your *buntu version..
But I suspect you need to use xorg-edgers ppa for intel & vaapi.
The default intel driver setup was partly disabled in ubuntu due to user problems. This situation may or may not be the case with ubuntu 12.04 & other variants..

I'm not a VLC user but could be useful to know where you sourced the vaapi version ..

---

### Post by raptir on 2012-04-16
Sorry, I'm running Xubuntu 12.04 currently. I will try updating to what is included in xorg edgers.

---

### Post by raptir on 2012-04-16
Oh, I was using the VLC version from the standard Ubuntu repository. 

Updating to edgers did not help with VLC. I did see some improvement with calling Mplayer with "-vo vaapi, xv". It plays 720p smoothly but still stutters somewhat on 1080p. However I also get the same CPU usage as if I call it with just "-vo xv", so maybe it's just falling back on xv? If I call it with just "-vo vaapi" I get no video. Also, I tried gnome-mplayer and smplayer and couldn't even get it to play with vaapi.

Any further suggestions? Thanks for all your help so far.

Edit: Yeah, it looks as though the mplayer in the repos does not support vaapi, so it's falling back to ffmpeg.

---

### Post by BicyclerBoy on 2012-04-16
I'm not a mplayer user either but..

You have to specify the video overlay/output/painter & the video codec..
VAAPI is an output & a decoder method.

mplayer -vo vaapi -vc vaapi

just using the -vo vaapi only prob. does help with all decoders tho..

You might have better success finding a daily/weekly build ppa of VLC/mplayer..
You need to disconnect your player from the packaged ffmpeg/libav* limitations etc.

---

### Post by raptir on 2012-04-16
So do none of the players that are in the main Ubuntu repository support vaapi? Do I need to find a ppa with a media player that supports it? I have no loyalty to gstreamer, mplayer, etc... I just want whatever is going to work for me the easiest.

---

### Post by BicyclerBoy on 2012-04-17
I don't know for sure..
I have not got to 12.04 & when using older versions (10.04) you have to build from source or find a ppa.

I would think that totem player would support vaapi if gstreamer does..

The std ubuntu apps use gstreamer & ffmpeg's/libav's libav* libraries..

It is possible to invoke gstreamer from cmd line to help debug..
A very basic start is
gst-launch playbin uri=file:///home/joe/my-random-media-file.mpeg


I have not found (or used) any test programs for va-api except from the original author:
[http://www.splitted-desktop.com/static/libva/hwdecode-demos/](http://www.splitted-desktop.com/static/libva/hwdecode-demos/)

---

### Post by raptir on 2012-04-17
Well, I went back to Windows to get the full DXVA support... and to be quite honest I can't stand it, at least on this computer. So I think I'll reinstall Ubuntu tomorrow and keep trying here. Apparently, mplayer-vaapi should do what I want (reading some other posts around the web, people seem to have some issues with gstreamer-vaapi and VLC but get great performance out of mplayer-vaapi). The Arch Linux package is build from this source:

[http://gitorious.org/vaapi/mplayer]("http://gitorious.org/vaapi/mplayer")

...however I don't honestly know how to install from source, or how to know what source code sources/ppas are safe. Is there any generic guide for building from source from git that you could link me to so I can try this? Thanks.

---

### Post by BicyclerBoy on 2012-04-18
PPA & launchpad ppa should be safe (comparatively).
I suppose private package archives could be compromised but they are digital signed.
The community would respond & take down any harmful ppa quite quickly..

This ppa seems safe..
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

If the code is sourced by tarball/zip etc you have little protection except your judgement.
If the code comes via git then you have some protection by looking at the host site.
github, gitorious, sourgeforge videolan LinuxTV.org kernel.org etc are safe. 

The best mplayer & vlc &ffmpeg building guides existed right here until a couple of weeks ago.

Check out the "Tips & Tutorials"
[http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

I think you can trust
andrew46
mc4man
thefakeoutdoorsman
(not an exhaustive list).

---

### Post by raptir on 2012-04-18
Well, I found this PPA, but I haven't seen any posts about people using it.

[https://launchpad.net/~sander-vangrieken/+archive/vaapi]("https://launchpad.net/~sander-vangrieken/+archive/vaapi")

I'll take a look at building it from gitorious tonight.

---

### Post by raptir on 2012-05-12
Sorry to bring up an old topic, but I had some issues with my laptop and finally got it replaced. I was not able to compile it successfully. It compiled, but I was not able to get any videos to 
play.

I did try the PPA from my last post in a test install, and it does work well, giving me the expected low CPU usage. But since I have not seen anyone else using said PPA, I'm not sure how reliable it is.

---

### Post by raptir on 2012-05-14
Okay, quick update here. I was able to get gstreamer to play the video with vaapi, and got the expected low cpu usage. I had to call it directly using:

```
gst-launch-0.10 -v filesrc location=~/test.mkv ! matroskademux ! vaapidecode ! vaapisink
```

However, I got no sound when I played it back this way. Still, a step in the right direction.

---

