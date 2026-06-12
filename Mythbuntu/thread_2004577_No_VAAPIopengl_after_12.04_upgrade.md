---
title: "No VAAPI/opengl after 12.04 upgrade"
date: 2012-06-16
forum: Mythbuntu
---

### Post by HTPCDIY on 2012-06-16
Before upgrading to Ubuntu 12.04 I had installed Mythbuntu 11.10 and everything was working fine. After 0.25 was released I upgraded to that with no problems. I followed the instructions at [http://www.mythtv.org/wiki/VAAPI](http://www.mythtv.org/wiki/VAAPI) and got VAAPI working fine on mythtv 0.25/ubuntu 11.10. Was able to get opengl, alpha pulse, better playback performance, etc.

After upgrading to 12.04 VAAPI and opengl no longer seem to work. I've seen numerous threads on the issue with no solution.

I'm using the onboard graphics z68 chipset:
```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```

I have tried to rebuild and reinstall the intel drivers in the VAAPI wiki article which at least got vainfo to return something.
libva: VA-API version 0.32.0
**libva: va_getDriverName() returns 0**
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so

output from vainfo:
```
**libva: va_openDriver() returns 0**
vainfo: VA-API version: 0.32 (libva 1.0.16.pre1)
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

When I run flgrxinfo I get:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

I see the same error as above when I run mythfrontend manually from the command line followed by: 
```
2012-06-16 01:22:39.577461 I  Trying the OpenGL painter
2012-06-16 01:22:39.582128 W  OpenGL: Could not determine whether Sync to VBlank is enabled.
2012-06-16 01:22:39.585186 E  Failed to create OpenGL painter. Check your OpenGL installation.
2012-06-16 01:22:39.585197 I  Clearing OpenGL painter cache.
2012-06-16 01:22:39.585271 I  Using the Qt painter

```

If I remember correctly that's the same error I get when trying to use the VAAPI playback profile.

Any thoughts how to get VAAPI working again?

---

### Post by BicyclerBoy on 2012-06-16
You have set the VAAPI profile to use the openglvaapi render ?
And set the OSD to opengl ?
AFAIK vaapi does not have any de-interlace post processing support yet..so is not usable for most broadcast TV..

The fglxinfo is AMD/ATI foo..
Use glxinfo & driconf for intel driver..


If you have doubts about your DIY intel driver try xorg-edgers ppa..

---

### Post by HTPCDIY on 2012-06-16
> **BicyclerBoy said:**
> You have set the VAAPI profile to use the openglvaapi render ?
And set the OSD to opengl ?
Yes I set both those up with mythbuntu 11.10 and they were both working fine. mythtv 0.25 comes with it's own VAAPI playback profile. I tried that one and the one that I had created. Neither worked.

> AFAIK vaapi does not have any de-interlace post processing support yet..so is not usable for most broadcast TV..

According to the full instructions the mythtv vaapi wiki was based on ([http://forum.xbmc.org/showthread.php?tid=114368](http://forum.xbmc.org/showthread.php?tid=114368)) the driver does have experimental support for bob deinterlacing. I don't know if it's only in XBMC though. I remember seeing some combing even after configuring VAAPI but I didn't notice it often enough to find it objectionable. The OSD without opengl was driving me crazy when tuned to an SD channel.

> The fglxinfo is AMD/ATI foo..
Use glxinfo & driconf for intel driver..

I didn't realize fglxinfo was different. glxinfo had the same exact output. 

I didn't install driconf until now and it's giving me an error "Screen 0 is not direct rendering capable." Since I posted last something else got screwed up.

> If you have doubts about your DIY intel driver try xorg-edgers ppa..

I was very confident about the intel driver I compiled since it was working fine under 11.10 It doesn't appear to be a mythtv issue either since I was running the latest 0.25 release before upgrading ubuntu and it was working fine. 

Something happened since I last posted. I tried a few different things including redownloading and recompiling the intel driver and libva. Now when I run vainfo it dumps core after the last VAProfile line with

```
*** glibc detected *** vainfo: free(): invalid next size (normal): 0x0000000000dc4de0 ***
```

Do you know of anyone using vaapi successfully with mythbuntu 12.04?

---

### Post by BicyclerBoy on 2012-06-17
Have a look in the log file /var/log/Xorg.0.log 
for any clues that the video driver is not loaded/running..
It sounds like the video driver is not right.

I sort of half-heartedly tried vaapi on vdpau h/w with 0.25 just to see if it worked..

There is a built-in VAAPI profile playback tester with myth 0.25+fixes..
It is posible that some de-interlacing is enabled..don't know.

I think one of the key VAAPI developers left the project.
VAAPI has been discussed recently on mythtv forums.

---

### Post by HTPCDIY on 2012-06-20
Ok here's some more info. Does it help anyone figure out a solution to my problem?

It looks like opengl is just not working for me after upgrading to 12.04. mplayer won't play in opengl either I get:

```
X11 error: BadRequest (invalid request code or no such operation)
X11 error: BadRequest (invalid request code or no such operation)
X11 error: BadRequest (invalid request code or no such operation)
[gl] no GLX support present
Error opening/initializing the selected video_out (-vo) device.
```

Here's some relevant parts from the XOrg log when I try and play a recording in mythtv using opengl. Getting a GLX Error: Can not get required symbols. 

```

 28.016] (II) intel(0): [DRI2] Setup complete
[    28.016] (II) intel(0): [DRI2]   DRI driver: i965
[    28.016] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, til
ed
[    28.017] (II) UXA(0): Driver registered support for the following operations
:
[    28.017] (II)         solid
[    28.017] (II)         copy
[    28.017] (II)         composite (RENDER acceleration)
[    28.017] (II)         put_image
[    28.017] (II)         get_image
[    28.017] (==) intel(0): Backing store disabled
[    28.017] (==) intel(0): Silken mouse enabled
[    28.017] (II) intel(0): Initializing HW Cursor
[    28.017] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.017] (==) intel(0): DPMS enabled
[    28.017] (==) intel(0): Intel XvMC decoder enabled
[    28.017] (II) intel(0): Set up textured video
[    28.017] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    28.017] (II) intel(0): direct rendering: DRI2 Enabled
[    28.017] (==) intel(0): hotplug detection: "enabled"
[    28.076] (--) RandR disabled
[    28.131] (II) Initializing built-in extension Generic Event Extension
[    28.131] (II) Initializing built-in extension SHAPE
[    28.131] (II) Initializing built-in extension MIT-SHM
[    28.131] (II) Initializing built-in extension XInputExtension
[    28.131] (II) Initializing built-in extension XTEST
[    28.131] (II) Initializing built-in extension BIG-REQUESTS
[    28.131] (II) Initializing built-in extension SYNC
[    28.131] (II) Initializing built-in extension XKEYBOARD
[    28.131] (II) Initializing built-in extension XC-MISC
[    28.131] (II) Initializing built-in extension SECURITY
[    28.131] (II) Initializing built-in extension XINERAMA
[    28.131] (II) Initializing built-in extension XFIXES
[    28.131] (II) Initializing built-in extension RENDER
[    28.131] (II) Initializing built-in extension RANDR
[    28.131] (II) Initializing built-in extension COMPOSITE
[    28.131] (II) Initializing built-in extension DAMAGE
[    28.132] (EE) GLX error: Can not get required symbols.

```

Not sure if this is relevant:
```


[    28.148] (II) config/udev: Adding input device HDA Intel PCH Front Headphone
 (/dev/input/event10)
[    28.148] (II) No input driver specified, ignoring this device.
[    28.148] (II) This device may have been added with another device file.
[    28.149] (II) config/udev: Adding input device HDA Intel PCH Line-Out Side (
/dev/input/event11)
[    28.149] (II) No input driver specified, ignoring this device.
[    28.149] (II) This device may have been added with another device file.
[    28.149] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event12)
[    28.149] (II) No input driver specified, ignoring this device.
[    28.149] (II) This device may have been added with another device file.
[    28.149] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/event13)
[    28.149] (II) No input driver specified, ignoring this device.
[    28.149] (II) This device may have been added with another device file.
[    28.149] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event14)
[    28.149] (II) No input driver specified, ignoring this device.
[    28.149] (II) This device may have been added with another device file.
[    28.149] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event6)
[    28.149] (II) No input driver specified, ignoring this device.
[    28.149] (II) This device may have been added with another device file.
[    28.150] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event7)
[    28.150] (II) No input driver specified, ignoring this device.
[    28.150] (II) This device may have been added with another device file.
[    28.150] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event8)
[    28.150] (II) No input driver specified, ignoring this device.
[    28.150] (II) This device may have been added with another device file.
[    28.150] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event9)

```

I tried running without VAAPI but with OpenGL, playback profile decoder standard, video renderer opengl, osd renderer opengl2 and I keep seeing this error whenever I try and play recordings.

```
Jun 13 01:54:19 mythtvbe1 mythfrontend[3038]: W CoreContext mythrender_opengl.cpp:65 (Create) OpenGL: Could not determine whether Sync to VBlank is enabled.
Jun 13 01:54:19 mythtvbe1 mythfrontend[3038]: E CoreContext videoout_opengl.cpp:326 (SetupContext) VidOutGL: Failed to create MythRenderOpenGL device.
Jun 13 01:54:19 mythtvbe1 mythfrontend[3038]: E CoreContext videooutbase.cpp:297 (Create) VideoOutput: Not compiled with any useable video output method.
Jun 13 01:54:19 mythtvbe1 mythfrontend[3038]: E CoreContext mythplayer.cpp:482 (InitVideo) Player(0): Couldn't create VideoOutput instance. Exiting..
Jun 13 01:54:19 mythtvbe1 mythfrontend[3038]: E CoreContext mythplayer.cpp:2679 (StartPlaying) Player(0): Unable to initialize video.

```

---

### Post by BicyclerBoy on 2012-06-21
glxinfo | grep OpenGL

does glxgears run ?

Seems like you don't have GL/GLX driver..I think va-api uses openGL for post processing & rendering.

---

### Post by HTPCDIY on 2012-06-21
> **BicyclerBoy said:**
> glxinfo | grep OpenGL

glxinfo gives this error 
```
$ glxinfo
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

> does glxgears run ?
No I get the same error as above

> Seems like you don't have GL/GLX driver..I think va-api uses openGL for post processing & rendering.

I'm really lost. I wish I would have run these commands on a working system to know what I should be expecting. Everything just worked on 11.10 :(

---

### Post by HTPCDIY on 2012-06-21
Got it working. Did a bunch of stuff before it but this is what fixed it [http://ubuntuforums.org/showpost.php?p=11600468&postcount=2](http://ubuntuforums.org/showpost.php?p=11600468&postcount=2)

For some reason something was set up to use fglrx This seems like a bug in the distro?

---

### Post by BicyclerBoy on 2012-06-21
Have you every had a AMD/ATI graphics card plugged in ?

Could have just been missing mesa..
You might not have installed the mesa packages because you built your own video driver..

---

### Post by HTPCDIY on 2012-06-21
> **BicyclerBoy said:**
> Have you every had a AMD/ATI graphics card plugged in ?

This is a brand new box that never had any other graphics card installed.

I had run sudo apt-get purge nvidia* or something like that. For some reason nvidia-common was installed.

> Could have just been missing mesa..

At one point or another during this whole mess I tried reinstalling opengl, mesa, xorg, the drivers, libva, mythtv and then some.

One of the commands I ran earlier today was :
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core

> You might not have installed the mesa packages because you built your own video driver..

Like I said, I had everything working in 11.10. I did a dist-upgrade to 12.04 without making any changes to the driver and that's when things got screwed up.

I don't know why you keep trying to blame it on something I might have done. Somewhere in the upgrade path from 11.10 to 12.04 openGL breaks when using SandyBridge processors and onboard intel graphics.

The sequence of events was:
- I installed Mythbuntu 11.10
- At some point I upgraded to MythTV 0.25
- Then I installed the intel drivers and libva as described in the mythtv wiki for VAAPI.
- Until I installed those drivers I do not think opengl was working at all but I may be wrong about that. I do know that after I did that opengl was working fine.
- At some point after Mythbuntu 12.04 came out I upgraded to it using sudo apt-get dist-upgrade

At this point OpenGL was no longer working.

I tried getting/compiling/installing new versions of the intel drivers and libva and that didn't work.

I tried installing the from the repos and even the ppn you suggested. That didn't work.

I reinstalled everything related to opengl, mythtv, libva, etc. that didn't work.

The only thing that worked was setting up the link properly.

I've seen a lot of people with similar problems. Do you know the appropriate place to report this issue?

---

### Post by BicyclerBoy on 2012-06-22
There is still sandybridge support code going into kernel 3.4..so the development is far from finished.
So is it really that surprising that something broke with 12.04 update..

I'm surprised that there is any vaapi functionality at all with HD2000/3000 & so quickly..just look at the GMA500 & now atom 2600 mess.

---

### Post by HTPCDIY on 2012-06-22
> **BicyclerBoy said:**
> So is it really that surprising that something broke with 12.04 update..

I didn't post here to express my surprise I posted to try and diagnose and fix a problem I and others had. I was also hoping that once a solution was found I could report it to the appropriate group so that it's not an issue for others.

But frankly I am a bit surprised considering Intel has been such a good open source contributor when compared to Nvidia. The solution I frequently heard was to buy an Nvidia card. The intel graphics are powerful enough to run mythtv and I wanted to keep my system as energy efficient as possible by using the onboard graphics.

---

### Post by anonymousdog on 2012-06-22
> **HTPCDIY said:**
> 
- Then I installed the intel drivers and libva as described in the mythtv wiki for VAAPI.

...at which point you stepped outside "the box" on this distro; so, resultant driver issues on a distro upgrade would not be a distro bug.  The upgrade process has no way to know how to upgrade that driver.

---

### Post by williammanda on 2012-06-24
My understanding about vaapi and sandy bridge is that it isn't complete or ready for prime time use in mythtv. I was one of many that was working with a mythtv developer that quit and from what I understand no other developer has stepped in to continue the work. Please see url:

[http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=502047;page=1;mh=-1;list=mythtv;sb=post_latest_reply;so=ASC](http://www.gossamer-threads.com/lists/engine?do=post_view_flat;post=502047;page=1;mh=-1;list=mythtv;sb=post_latest_reply;so=ASC)

For the last few months I have been using one of the opengl profiles and I am very pleased with the performance. This doesn't satify the energy issue but for now it works with mythtv and possibly in the future mythtv will get there if not torc is another avenue.

---

### Post by andree_b on 2012-06-27
I read somewhere the frglx AMD/ATI driver overwrites the system libgl with a proprietary one, that seems to be the main cause for the effect (no working opengl etc.) for the OP.

The frglx driver should have not been installed at all on his box anyhow, but it seems it got installed during dist upgrade or manual upgrade steps, may be because wrong dependencies of libva for example. 
So this might be a packaging/distribution problem too.

---

