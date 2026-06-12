---
title: "HOWTO: VLC + VAAPI in Maverick"
date: 2010-10-04
forum: Multimedia Software
---

### Post by AdrianVeidt on 2010-10-04
I thought I would go over some of the basics. In a nutshell, most graphics chips made in the past couple of years now have the ability to accelerate h.264 and wmv3 at the very least through va-api and VLC in Maverick.

Now, when you ask for VLC to be installed, va-api, which is called "libva", will be installed with it. That library then needs one of three possible video drivers to be present to work. Two of the three driver packages are already in Maverick too. They are vdpau-va-driver (for Nvidia chips) and i965-va-driver (for Intel chips). The third package, for ATI/AMD chips, is called xvba-video. You will have to go here:
[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)
grab the latest package for your arch. Download and double-click it and it will offer to install itself.

Now, to be clear, the proprietary nvidia and AMD drivers must be activated and in use for this to work on those platforms. The open-source drivers do not support video acceleration on Nvidia/AMD at this point in time. Only very new Intel hardware is supported, from the GMA4500 onwards.

So to summarize -- If you have an nvidia graphics platform:

```

$sudo apt-get install vlc vdpau-va-driver
```

VLC must be told to use va-api. Open VLC, click Tools>Preferences>Video, and check "Accelerated Video Output". Furthermore, video filters/effects and deinterlacing will be done by the CPU, so turn these off for maximum effect.

---

### Post by mc4man on 2010-10-05
> Tools>Preferences>Video, and check "Accelerated Video Output"
That should be on vaapi or not, for vaapi it's enabled in 'Input and Codecs' - 'Use GPU acceleration'

(I'd suggest d. checking in htop if it is providing any benefit, certainly possible w/ some sources & hardware compo's that cpu use will increase w/ vaapi

---

### Post by insaini on 2010-10-11
im having issues for some reason.. vlc is seg faulting..

i installed vainfo 

getting this

```
libva: libva version 0.31.1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
Segmentation fault
```

maverick 64bit
nvidia 8600 GTS

---

### Post by insaini on 2010-10-11
seems like libva in the xorg edgers ppa isnt updated yet.. had to purge the ppa.. works now

---

### Post by sizeak on 2010-10-11
I keep getting issues related to libva-glx being missing but I can't for the life of me find it anywhere. It doesn't seem to be in the repo when I apt-cache search it. Any ideas?

---

### Post by bsmith1051 on 2010-11-04
> **AdrianVeidt said:**
> Two of the three driver packages are already in Maverick too. They are vdpau-va-driver (for Nvidia chips) and i965-va-driver (for Intel chips). The third package, for ATI/AMD chips, is called xvba-video. You will have to go here:
[http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)

Thank you! This is exactly the information I needed.  Now, off to try it...

UPDATE: it doesn't work.  When I run 'vainfo' it reports,
```
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```

Any suggestions?  This is on Ubuntu 10.10 (AMD64) with an ATI 4200 and the latest Catalyst 10.10 (as provided automatically by the Ubuntu 'Hardware Drivers' installer)

---

### Post by .... on 2010-11-04
> **sizeak said:**
> I keep getting issues related to libva-glx being missing but I can't for the life of me find it anywhere. It doesn't seem to be in the repo when I apt-cache search it. Any ideas?
It's a little tougher with ATI/XvBA. You have to extract a couple files (libva-glx) out of the ATI Catalyst installer and use the libva from splitted-desktop. Even then, it's not perfect.

---

### Post by rbflut on 2010-11-06
I also am attempting to get VA-API working in VLC on a Radeon 3200 integrated graphics chip. I also got the error :

```
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
```[FONT=Verdana]I was able to fix that error from vainfo by installing libva1 from [http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/amd64/]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/amd64/") over top of the ubuntu package, but when I run vlc from Termial, I get the same "libva: va_getDriverName() returns -1"  what could still be causing that?[/FONT][FONT=monospace][FONT=Verdana]
[/FONT] 
[/FONT]

---

### Post by screaminj3sus on 2010-12-06
bump, I get the same error as the post above trying to get this working with an ati card using fglrx 10.11, ubuntu 10.10 64 bit, radeon hd2600.

---

### Post by bsmith1051 on 2010-12-07
> **screaminj3sus said:**
> bump, I get the same error as the post above trying to get this working with an ati card using fglrx 10.11, ubuntu 10.10 64 bit, radeon hd2600.
I don't think you can do it with your hardware?  I thought that only the HD3x00 series (on up) were supported for h.264 acceleration.  I might be wrong, though, so check around.

---

### Post by screaminj3sus on 2010-12-07
> **bsmith1051 said:**
> I don't think you can do it with your hardware?  I thought that only the HD3x00 series (on up) were supported for h.264 acceleration.  I might be wrong, though, so check around.

My card definitely supports it. I can use dxva in windows just fine. I actually did get it to work after a long time messing around with packages and I managed to find the libva-glx package in a ppa. I was able to get vlc to load the video up and have vaapi acceleration enabled but the output was all garbled :/.

It was just the hd 2900 cards that did not have the capability, they were the first 2xxx card released. other 2xxx cards do have it. In windows 7 I use MPC-HC and dxva is enabled, and 720p videos play with only 2-4% cpu usage.
[http://en.wikipedia.org/wiki/Radeon_R600#Video_processing.2C_display_and_miscellaneous_features](http://en.wikipedia.org/wiki/Radeon_R600#Video_processing.2C_display_and_miscellaneous_features)

---

### Post by bsmith1051 on 2010-12-09
I realize the HD 2600 is physically capable of h.264 acceleration but there's a lot more support under Windows than under Linux; that's what I meant.

I followed-up and checked the ATI/AMD downloads and, yes, their Linux driver supports the HD 2x00 series. Sorry, still don't know how to help you, though...

---

### Post by beew on 2010-12-11
It doesn't work for me. I have a Nvidia card and have installed the driver and the vdpau-va-driver. Checked "Accelarated Video Output" and also "Use GPU Accelaration" in  "Input and Codecs" but it makes no difference. Still using the same amount of cpu (~60% for 1080p) 

I know vdpau works for my card and Ubuntu 10.10  because it works spectacularly for mplayer. For the same files if mplayer's video output is set to "xv" it uses roughly the same cpu respources as VLC, but with output switched to vdpau it drops to 10~ 15%. For 720p it is under 10% for mplayer with vdpau but VLC still uses 30 to 40%.

---

### Post by .... on 2010-12-12
> **beew said:**
> It doesn't work for me. I have a Nvidia card and have installed the driver and the vdpau-va-driver. Checked "Accelarated Video Output" and also "Use GPU Accelaration" in  "Input and Codecs" but it makes no difference. Still using the same amount of cpu (~60% for 1080p) 

I know vdpau works for my card and Ubuntu 10.10  because it works spectacularly for mplayer. For the same files if mplayer's video output is set to "xv" it uses roughly the same cpu respources as VLC, but with output switched to vdpau it drops to 10~ 15%. For 720p it is under 10% for mplayer with vdpau but VLC still uses 30 to 40%.
What does vainfo command show?

---

### Post by Yellow Pasque on 2010-12-12
> **.... said:**
> What does vainfo command show?
^If you're using nvidia vdpau, you still need to install the version of libva found at splitted-desktop site in addition to va-vdpau.

---

### Post by beew on 2010-12-12
> **.... said:**
> What does vainfo command show?

Here it is

> libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA API - 0.6.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

---

### Post by mc4man on 2010-12-12
> **beew said:**
> It doesn't work for me. I have a Nvidia card and have installed the driver and the vdpau-va-driver. Checked "Accelarated Video Output" and also "Use GPU Accelaration" in  "Input and Codecs" but it makes no difference..

You shouldn't need to go outside to enable as long as your ffmpeg libs and vlc are vaapi enabled. (libva1, vdpau-va, and maybe libva-x11-1

To test your vlc/ffmpeg libs in a terminal this, should come up clean 
```
vlc --ffmpeg-hw
```

vainfo should show in part
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0

Ex. ( heavily clipped from vlc -vvv
> [0x8a61d7c] avcodec decoder debug: Available decoder output format 53 (PIX_FMT_VAAPI_VLD)
[0x8a61d7c] avcodec decoder debug: Trying VA API
[0x87ea52c] main input debug: Buffering 100%
ibva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
[0x8a61d7c] avcodec decoder: Using VA API version 0.31 for hardware decoding.


I'd say the performance gotten would most likely will be dependant on your hardware and to a degree the source material, for the most part here no big deal, maybe 35 - 50 % reduction, if that, compared to mlayer/vdpau which is in the 80 - 90 % range.
(though I'd take my results w/ a large grain of salt, the card here on this laptop is only minimally enabled in this area.

I would certainly try the ubuntu libs first, then maybe any outside versions if desired.

If your vlc is deficient, (never used mav's version), then you may want to build your own or  entertain this ppa, (updates frequently), some -r's may have small regressions 
[https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)

Edit: small note about the ppa - the build today failed due to a new plugin, no big deal, someone will adjust the vlc-nox install file soon to reflect this. (prior build from a day or so ago is still available

---

### Post by beew on 2010-12-12
Hi, mc4man
```

vlc --ffmpeg-hw 
```

produces the following (and vlc opens)
> VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb71ff0d4, 0xb71ff048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1292889795)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:29154): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)



What do these mean?

My vainfo output is above your post.

---

### Post by mc4man on 2010-12-12
> What do these mean?
That means vlc/ffmpeg libs are vaapi enabled. Why don't you try 
vlc -vv /path/to/video
where the video file chosen can be decoded w/ vaapi (h.264 would be good.

Then stop the playback/close vlc and search thru the terminal output to see if vaapi is being used. (look for similar lines as I posted, note -vv produces a fair amount of output.
You can use the search -> find function in the terminal to make it quicker to locate, search VA API or similar

( as mentioned I don't find vaapi in vlc to be worth it w/ my hardware

---

### Post by SkylinesSuck on 2010-12-30
Any way to make this work with 10.4?  I can't upgrade to 10.10 on this netbook (1.3ghz AMD dual core, ATI HD 4225 GPU, 4gb ram) do to hardware issues, and I cant get 1080p stuff to play smoothly in Ubuntu, but it works fine with Win 7.  This is killing me.  I've love to get 1080p working in Lucid so I can strip winblows off this netbook for good.

> The third package, for ATI/AMD chips, is called xvba-video. I tried to find this pluggin but I couldn't fin it in synaptic anywhere.  Where else should I look?  Is it only a 10.10 thing?  Im using vlc 1.1.5 in 64 bit lucid BTW.

---

### Post by Yellow Pasque on 2010-12-30
Skylines, it's not pretty.
First, you'll need to install the latest Catalyst. Follow the removal procedure to get rid of your old driver first. Then follow the manual installation guide: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

Once you have Catalyst 10-12 running, you'll need libva, libva-dev, and xvba-video packages from: [http://www.splitted-desktop.com/~gbeauchesne/](http://www.splitted-desktop.com/~gbeauchesne/)

After that, you'll need to find a way to rebuild VLC (or another vaapi-enabled player) against the new libraries. There is a PPA that does a lot of the heavy lifting, but I do not know if it works: [https://launchpad.net/~ed10vi86/+archive/video](https://launchpad.net/~ed10vi86/+archive/video)

---

### Post by SkylinesSuck on 2010-12-31
Thanks for the reply.  I actually managed to get 10.12 up and running---which gave me HDMI out sound (only system sounds though, not movies :confused: ) but I hadn't started on the rest of it yet.  I'll get to reading and I'm sure I'll be back with more questions.  Thanks again and Happy New Years! ):P (It's already 2011 here)

---

### Post by SkylinesSuck on 2011-01-02
So during my re-install of ATI 10.12 catalyst the guide I was following ) __[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) ) mentions something called libamdxvba1 saying:

 > 16. Now "libamdxvba1" is optional but since it provides some aspects of the AMD Unified Video Decoder it may be of some use. ([http://en.wikipedia.org/wiki/Unified_Video_Decoder](http://en.wikipedia.org/wiki/Unified_Video_Decoder)).     

but that's all they say about it.  In the wikipedia link provided it sys my Radeon HD 4225 supports UVD 2.0 so the hardware acceleration is possible it would seem.  Any ideas on how to see if that is up and running on my system and how I could enable it if not?

---

### Post by mr_raider on 2011-01-03
So after a lot of screwing around this is what I get from vainfo:

> 
libva: libva version 0.31.1-sds1
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.7
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD


I'm using 10.10 with catalys 10.12, xvba 0.7.7 from splitted desktops, and finally got a version of libva1 that doesn't throw an error. GPU is a mobility Radeon 3400 (RV 620).

VLC still has high cpu usage during playback though.

---

### Post by Yellow Pasque on 2011-01-03
^You'll need to rebuild vlc once you have the new libva-dev installed (or you can use my new PPA where it's already done for you: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks) )

---

### Post by mr_raider on 2011-01-03
> **Temüjin said:**
> ^You'll need to rebuild vlc once you have the new libva-dev installed (or you can use my new PPA where it's already done for you: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks) )

Thanks that help. I can now play with VAAPI in VLC, but the output is garbled and a messed up colors! Same think in XBMC, though my CPU use is very low!

This is with a x264 file. I have to try VC1.

---

### Post by Yellow Pasque on 2011-01-03
xvba is broken for older RadeonHD cards (2000 and 3000 series). Catalyst 10-7 was the last blob reported working.

---

### Post by mr_raider on 2011-01-03
So I patiently wait for the fix?

Last I checked 10.7 didn't compile on 2.6.35

---

### Post by Yellow Pasque on 2011-01-03
:\ I didn't know that. If I find the appropriate patches, I'll let you know. It would be far better if ATI fixed the issue in an upcoming Catalyst.

---

### Post by koda on 2011-02-09
i was able to enable vaapi only with the latest libva sources and the latest drivers compiled against it.

then again, most of the videos crashed with it, so i'd have been better off

VDPAU was so much better.................................................

---

### Post by hachel on 2011-02-09
so i've updated to the newest flash (10.2) with GPU-Acceleration and am henceforth able to play even videos with a hd-resultion of 1080p ([this video]("http://www.youtube.com/watch?v=_iRPWD6imV8")), while my cpu usage doesn't exceed 50%.
I have just followed your howto and in the process enabled GPU in Preferences->Input/Codecs->Use GPU Acceleration.
Yet, when I download that same Video and play it in VLC it doesn't work at all (cpu at 100%, a new frame every 10-20 seconds). I guess thats because it's in that flv-container.
But even if I download an mp4/h264-Video in 1080p it has occasional stutters and cpu on average between 85 and 95%.
How is it that flash works so much better, when before 10.2 I couldn't even play 480p-Videos flawlessly? Anyway to improve vlc-performance?

---

### Post by SirBelial on 2011-04-23
I installed the newest ATI Driver (Catalyst 11.3 / 8.83) with tutorial from wiki.cchtml. Then I installed libva, libva-dev, libva-dbg and  xvba-video from splitted-desktop.
vainfo says:
```
libva: libva version 0.32.0-sds2
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

```So it seems to be kind of working.
Next I installed vlc with the PPA by Temüjin but when I try to open a video file (both .avi and .mkv) it says:
```
[COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "mp4v". Unfortunately there is no way for you to fix this.[/COLOR]
 [COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "h264". Unfortunately there is no way for you to fix this.[/COLOR]

```Can you see anything I did wrong?

I'm using:
AMD Athlon Neo Processor MV-40 1.6 GHz | 3GB DDR2 RAM | AMD ATI Mobility Radeon HD3200 | Ubuntu Maverick

---

### Post by Yellow Pasque on 2011-04-23
> **SirBelial said:**
> AMD ATI Mobility Radeon HD3200 
from the wiki...
> If you have an older RadeonHD with UVD, you can use Catalyst 10-7 to get working acceleration, but users have confirmed acceleration broken since then. 

Unfortunately, this applies to your GPU. :(

---

### Post by SirBelial on 2011-04-23
Crap, that's what I feared when I started reading about UVD.
I'm thinking about sending back the ThinkPad X100e with a single core to get one with a dual core (2x 1,6Ghz). Do you think that the new CPU will be enough to at least decode 720p mkvs?

---

### Post by SirBelial on 2011-04-24
Another question:
what is the weak link in the chain that doesn't make it work?
The GPU is able to do video decode acceleration, since it works with Windows 7 and DxVA.
So what's the problem? Catalyst? Any of the packages?
(I don't have a good understanding on how it's supposed to work)
So is there a possibility that in the future this weak link will be expanded to include GPUs with UVD(1)?

---

### Post by Yellow Pasque on 2011-04-25
> **SirBelial said:**
> what is the weak link in the chain that doesn't make it work?
UVD cards worked as well as UVD2 until Catalyst 10-8, so something changed there. Oddly enough, I don't see a bug report for it on AMD's bugzilla, but it's a well-known issue.

You're guess is as good as anyone's when/if it will be fixed.

---

### Post by nefan on 2011-05-21
On my HP dm1 with AMD Fusion, I installed libva1, libva1-dev, and vlc from [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks) and xvba_video from [http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/) . After adding a symlink and setting LIBVA_DRIVER_NAME to fglrx (or xvba), vainfo works and gives 

ibva: libva version 0.32.0-sds2
libva: User requested driver 'fglrx'
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.32
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD


However, vlc fails to use va-api and outputs

libva: libva version 0.32.0-sds2
libva: User requested driver 'fglrx'
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
[0x3460300] avcodec decoder warning: Failed to open VA API


Any ideas?

---

### Post by wringles on 2011-05-22
> **nefan said:**
> However, vlc fails to use va-api and outputs

libva: libva version 0.32.0-sds2
libva: User requested driver 'fglrx'
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
[0x3460300] avcodec decoder warning: Failed to open VA API


Any ideas?

Ok, this is a very idiotic question, but have you already installed fglrx? I'd used the method you have described, and (crazily) the drivers in catalyst-hacks **do not** depend on fglrx.

---

### Post by nefan on 2011-05-23
thanks, but fglrx is installed. /usr/lib/va/drivers/fglrx_drv_video.so is a symlink to xvba_drv_video.so - I'm not sure if that is right. If I set LIBVA_DRIVER_NAME to xvba instead of fglrx, I get

libva: libva version 0.32.0-sds2
libva: User requested driver 'xvba'
libva: Trying to open /usr/lib/va/drivers/xvba_drv_video.so
libva: va_openDriver() returns 0

i.e, it now tries to open /usr/lib/va/drivers/xvba_drv_video.so . I'm not sure I use LIBVA_DRIVER_NAME correctly but if I don't set it, vlc segfaults.

---

