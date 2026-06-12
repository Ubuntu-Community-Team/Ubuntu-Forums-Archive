---
title: "Nvidia VDPAU PPA"
date: 2010-09-01
forum: Multimedia Software
---

### Post by vbsaltydog on 2010-09-01
I am a bit confused here regarding the NVIDIA drivers. I am trying to get two things working under lucid.

1. Mplayer/SMPlayer for HD mkv files with VDPAU.
2. MythTV with VDPAU.

I have enabled the NVIDIA PPA and the X-SWAT PPA but here is the first bit of confusion:

There is an nvdia ppa , and nvidia-vdpau ppa, and an x-swat ppa and they all claim to have the nvidia drivers. Which one has the right ones? I know the current release is the 256 drivers but why three repos all claiming to have the nvidia drivers and they all have different debs listed?

Next, all of the how to's just say to enable the PPAs and install the drivers but there are a lot of debs in each repo and there are three repos. Which debs do you need to install from which repo(s)?

After you download whatever debs, how do you know that the nvidia drivers are installed correctly, and that vdpau is supported?

I installed a bunch of debs from the repos that looked relevant and set the nvidia current drivers in the lucid hardware drivers utility, enabled the nvidia drivers for X and rebooted, all seems fine and I get output when running the vdpauinfo command but I have no idea if I installed the right drivers, from the right sources, in the right order.

Can anybody shed some light on how the nvidia drivers/ppa installs are supposed to work beyond that of just enable the repo and install which is incomprehensibly vague given the number of repos and the number of debs per repo?

Thank you

---

### Post by cchhrriiss121212 on 2010-09-01
If you are using 10.04 then you do not need to use any PPAs, just install regular smplayer and select vdpau ouput, after installing an nvidia driver.
> After you download whatever debs, how do you know that the nvidia drivers are installed correctly, and that vdpau is supported?
Try running nvidia-settings in a terminal to check your driver, if you don't find it you can install it from the repos. I think vdpau works for drivers 185 and upwards. To check if you have vdpau installed correctly just try it out with smplayer, you should get smooth output and very low cpu usage.

Regarding your PPA confusion: PPAs are personal package archives, which means that they are all maintained by different individuals (i.e. not Ubuntu), this is why you see various PPAs that have the same things. Use PPAs at your own risk, and install as few of them as possible, as they can cause conflicts with each other.

---

### Post by sojusnik on 2010-09-02
Well, it seems that it's not that easy with vdpau.

I've tried several methods, all of which failed to run a HD video file smoothly in lucid.

1. Installed smplayer und libvdpau from the default ubuntu lucid repos without adding any special ppa.

2. Used this ppa ([https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)) to install a newer SMPlayer version with default lucid libvdpau.

3. Used this ppa ([https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)) to install a newer version of libvdpau, named libvdpau1.

In SMPlayer the video output driver is set to vdpau and the audio driver to pulse.

Everytime I want to open a .mkv HD video file, SMPlayer crashs after some time of loading the video. My video card (Nvidia 8400M GT) seems to support vdpau. I have the latest nvidia drivers installed from the ubuntu repo (195.36.24) running on a 64-bit system.

When selecting XV in the video output driver, all .mkv videos are running well, but the CPU is at 100% and the HD video playback is choppy.

Maybe I have to adjust some settings in SMPlayer for vdpau video playback?

Did I forget any vital settings to make vdpau run properly in lucid?

Any hints where I can find additional information on this issue?

Is it worth to try to install the new 256.52 nvidia driver from this ppa ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates))?

Thanks in advance for assisting!

---

### Post by vbsaltydog on 2010-09-02
Here is what I did that works for me and should work for you too with the exception of your card. I think you might need to double check that your card supports vdpau. There was something that i read about the nvidia version numbering and vdpau support that suggests your card MIGHT not be vdpau compliant so you should double check.

####
## That is a start to finish guide to install/upgrade/configure nvidia vdpau support
## for the mplayer video backend and smplayer video frontend under Ubuntu Lucid Lynx
## for smooth playback of HD content. Note: This guide requires a video card with the 
## nvidia 8xxx or better chipset.
####

## Here is what I have done to get h264 video ( mkv files ) playing smoothly on a single core 2.4 box:

####
## Install and update Ubuntu
####

1. Fresh Lucid install
2. apt-get update
3. apt-get upgrade

####
## Enable the default nvidia drivers
####

4  System > Administration > Hardware Drivers > Enabled the Nvidia Current (which was 195 series)
5. Reboot

####
## Update the nvidia drivers
####

6. apt-add-repository ppa:ubuntu-x-swat/x-updates
7. apt-get update
8. apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
9. Reboot
10. System > Administration > NVidia Settings > Check the version and make sure it is 256 (as of this writing)

####
## Install and configure mplayer
####

11. apt-add-repository ppa:nvidia-vdpau/ppa
12. apt-get update
13. apt-get install mplayer
14. vi ~/.mplayer/config
15. Edit  the  config file to add: 
vc=ffh264vdpau
vo=vdpau

####
## Install and configure smplayer
####

16. apt-get install smplayer
17. Within the smplayer GUI, options > preferences > video > change output to vdpau

####
## Configure the X Server to fix video tearing during playback
####

18. vi /etc/X11/xorg.conf
19. Edit the xorg.conf file and add the following:
Section "Extensions"
        Option         "Composite" "Disable"
EndSection
20. Reboot

####
## Finished
####

---

### Post by sojusnik on 2010-09-02
Hi,

I've installed the new nvidia driver (256) via ppa:ubuntu-x-swat/x-updates. Still no improvement.

But maybe I've noticed something useful.

Opening a video file with

> mplayer /home/sojusnik/Downloads/Fireplace.mkv

gives the following

> 
MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/sojusnik/Downloads/Fireplace.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Track ID 3: audio (A_AC3), -aid 1, -alang und
[mkv] Track ID 4: audio (A_AC3), -aid 2, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
[ASPECT] Warning: No suitable new res found!
A:  23.3 V:  23.3 A-V:  0.000 ct:  0.000   0/  0 89%  4%  0.6% 6 0 

MPlayer interrupted by signal 2 in module: sleep_timer
A:  23.3 V:  23.3 A-V:  0.000 ct:  0.000   0/  0 89%  4%  0.6% 6 0 
Exiting... (Quit)


Opening the same file with

> mplayer -vo vdpau -vc ffh264vdpau /home/sojusnik/Downloads/Fireplace.mkv

results in

> [h264_vdpau @ 0x7f325a9e99a0]no frame!
Error while decoding frame!
[h264_vdpau @ 0x7f325a9e99a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f325a9e99a0]decode_slice_header error
[h264_vdpau @ 0x7f325a9e99a0]no frame!
Error while decoding frame!
.
.
.
[h264_vdpau @ 0x7f325a9e99a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f325a9e99a0]decode_slice_header error
[h264_vdpau @ 0x7f325a9e99a0]no frame!
Error while decoding frame!
[h264_vdpau @ 0x7f325a9e99a0]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f325a9e99a0]decode_slice_header error
[h264_vdpau @ 0x7f325a9e99a0]no frame!
Error while decoding frame!

Too many audio packets in the buffer: (4103 in 3151104 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)


It seems that my graphic card is supported as you can [read here]("http://www.mythtv.org/wiki/VDPAU").

libvdpau1 is also properly installed as I think. Entering "vdpauinfo" in the shell shows:

> display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  256.52  Wed Aug 25 14:39:25 PDT 2010

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                 0  8192  2048  2048
MPEG2_SIMPLE          3  8192  2048  2048
MPEG2_MAIN            3  8192  2048  2048
H264_MAIN            41  8192  2048  2048
H264_HIGH            41  8192  2048  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  


Any further hints?

---

### Post by vbsaltydog on 2010-09-02
Try a different mkv file.

---

### Post by sojusnik on 2010-09-02
The drivers are installed well, because nvidia-settings is showing the latest (256.52) driver version.

vdpauinfo information was posted the second you wrote your post :)

---

### Post by sojusnik on 2010-09-02
Opening another .mkv file, not HD, with the following command, gives sound but choppy and completly destroyed video picture.

> sojusnik@cassiopeia:~$ mplayer -vo vdpau -vc ffh264vdpau /home/sojusnik/Videos/12.mkv
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.
[vdpau] Failed VDPAU decoder rendering: An invalid handle value was provided.
[vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: A catch-all error, used when no other error code applies.
[vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.


MPlayer interrupted by signal 2 in module: sleep_timer
[vdpau] Error when calling vdp_video_surface_destroy: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_surface_destroy: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_surface_destroy: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_surface_destroy: An invalid handle value was provided.
[vdpau] Error when calling vdp_video_surface_destroy: An invalid handle value was provided.
[vdpau] Error when calling vdp_output_surface_destroy: An invalid handle value was provided.
[vdpau] Error when calling vdp_output_surface_destroy: An invalid handle value was provided.

Of course all these .mkv files are properly played with XV, that works well with non HD videos, but is CPU-consuming with HD videos.

---

### Post by vbsaltydog on 2010-09-03
This might be because you forced mplayer to use the codec of ffh264vdpau and you said it was not an H.264 or X.264 encoded file.

Here is a link to a blog I started that shows the steps I used to build my HD playback / MythTV box including the steps for vdpau, mplayer, smplayer, mythtv, and lirc for remote control over all of the multimedia playback programs.

[Ubuntu MythTV Build]("http://www.cartmod.com/howto/?p=5")

---

### Post by sojusnik on 2010-09-03
Hi,

I've downloaded the opensource movie Big Buck Bunny in 1080p h.264 quality to make another test, but sadly I get the same outcome.

I've managed to copy also the first part of the terminal output when opening this movie, because my terminal showed me only the last part of it before.

> sojusnik@cassiopeia:~$ mplayer -vo vdpau -vc ffh264vdpau /home/sojusnik/Desktop/bunny.mov

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing /home/sojusnik/Desktop/bunny.mov.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 2
VIDEO:  [avc1]  1920x1080  24bpp  24.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Forced video codec: ffh264vdpau
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffh264vdpau] vfm: ffmpeg (FFmpeg H.264 (VDPAU))
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 1920 x 1080 (preferred colorspace: H.264 VDPAU acceleration)
VDec: using H.264 VDPAU acceleration as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [vdpau] 1920x1080 => 1920x1080 H.264 VDPAU acceleration 
[ASPECT] Warning: No suitable new res found!
[vdpau] Failed creating VDPAU decoder: The system does not have enough resources to complete the requested operation at this time.
FATAL: Cannot initialize video driver.
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]no frame!
Error while decoding frame!
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]no frame!
Error while decoding frame!
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]B picture before any references, skipping
[h264_vdpau @ 0x7fb931632840]decode_slice_header error
[h264_vdpau @ 0x7fb931632840]no frame!
Error while decoding frame!
.
.
.
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]B picture before any references, skipping
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]no frame!
Error while decoding frame!
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]get_buffer() failed (-1 0 0 (nil))
[h264_vdpau @ 0x7f9073f9a840]decode_slice_header error
[h264_vdpau @ 0x7f9073f9a840]no frame!
Error while decoding frame!

Too many audio packets in the buffer: (4096 in 4777088 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)

Does this output help us to find the solution?

---

### Post by vbsaltydog on 2010-09-03
This looks like a pretty good place to start debugging:

```

[vdpau] Failed creating VDPAU decoder: The system does not have enough resources to complete the requested operation at this time.
FATAL: Cannot initialize video driver.

```

What are your system specs?

---

### Post by sojusnik on 2010-09-03
I think my system should easily manage this process:

Processor: 2x Intel(R) Core(TM)2 Duo CPU T7250 @ 2.00GHz
Memory: 2062MB
Graphics: GeForce 8400M GT/PCI/SSE2

---

### Post by vbsaltydog on 2010-09-03
According to the output from mplayer, your system does not have the resources to process the video file with the vdpau driver so I would look at the output from the top command in a separate terminal while firing up mplayer on the video file and see what my usage specs are.

---

### Post by sojusnik on 2010-09-04
I've started the video file via the following command and made a screenshot of top while doing so.
> mplayer -vo vdpau -vc ffh264vdpau /home/sojusnik/Desktop/bunny.mov

Link to top screenshot: [http://www.box.net/shared/cg314lfc14](http://www.box.net/shared/cg314lfc14)

I can't detect any suspicious signs...

---

### Post by sgtGarcia on 2010-09-04
You probably have 256MB VRAM on the graphic card. This is probably Your problem. 256MB is minimum needed for VDPAU, but some of this memory is occupied by Your screen.

---

### Post by sojusnik on 2010-09-04
Hmm, but my 2 GB Ram are never used fully. Normally, only ~700MBs are used, so there must be enough memory left for the graphic card. I've checked my BIOS and there is no setting for adjusting shared memory of the graphic card.

As it is stated in this list, my graphic card should suffice for vdpau:
[ftp://download.nvidia.com/XFree86/Linux-x86/195.36.15/README/supportedchips.html](ftp://download.nvidia.com/XFree86/Linux-x86/195.36.15/README/supportedchips.html)

Any suggestions?

---

### Post by vbsaltydog on 2010-09-04
> **sgtgarcia said:**
> you probably have 256mb vram on the graphic card. This is probably your problem. 256mb is minimum needed for vdpau, but some of this memory is occupied by your screen.

+1

---

### Post by sgtGarcia on 2010-09-04
But VDPAU don't use main RAM it use graphic ram & I don't know if it could use main ram ( as far as I remember it's only possible with integrated graphic controllers where You can set the main memory be accessible via IGP and thus VDPAU).

Edit:

Yes, Your chip is capable of CUDA/VDPAU but VRAM is not enough for this to work.

---

### Post by sojusnik on 2010-09-04
So with my graphic card it's not possible to watch HD video with vdpau support?

---

### Post by vbsaltydog on 2010-09-04
> **sgtGarcia said:**
> But VDPAU don't use main RAM it use graphic ram & I don't know if it could use main ram ( as far as I remember it's only possible with integrated graphic controllers where You can set the main memory be accessible via IGP and thus VDPAU).

Edit:

Yes, Your chip is capable of CUDA/VDPAU but VRAM is not enough for this to work.

Agreed. You may have 2g of main system RAM but vdpau is basically a "device" where video processing occurs and where the video is output to so when you have your x server using vdpau and your mplayer using vdapu for its output then ALL of your system's video is going out through the vdpau "device" and this may be overwhelming the onboard RAM of your graphics card while not using any of the main system RAM.

What are the contents of your /etc/X11/xorg.conf ? Perhaps you can offload some of the video processing (desktop) to the main system board's RAM.

---

### Post by sojusnik on 2010-09-04
xorg.conf:

> Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	# added manually:
	Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection

---

### Post by vbsaltydog on 2010-09-04
What about the output of vdpauinfo while you fire up mplayer on the mkv file? 
That might shed more light on what vdpau is choking on.

---

### Post by sojusnik on 2010-09-04
The vdpauinfo is not changing when launching the file via shell. It always stays as you can see it here:

> sojusnik@cassiopeia:~$ vdpauinfo
display: :0.0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  256.52  Wed Aug 25 14:39:25 PDT 2010

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name               level macbs width height
-------------------------------------------
MPEG1                 0  8192  2048  2048
MPEG2_SIMPLE          3  8192  2048  2048
MPEG2_MAIN            3  8192  2048  2048
H264_MAIN            41  8192  2048  2048
H264_HIGH            41  8192  2048  2048
VC1_SIMPLE            1  8190  2048  2048
VC1_MAIN              2  8190  2048  2048
VC1_ADVANCED          4  8190  2048  2048

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8          8192  8192    y  Y8U8V8A8 V8U8Y8A8 
R10G10B10A2       8192  8192    y  Y8U8V8A8 V8U8Y8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8          8192  8192
R8G8B8A8          8192  8192
R10G10B10A2       8192  8192
B10G10R10A2       8192  8192
A8                8192  8192

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        -
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  

---

### Post by vbsaltydog on 2010-09-04
Take your only known error to Google and see what you can find:

[vdpau] Failed creating VDPAU decoder: The system does not have enough resources to complete the requested operation at this time.
FATAL: Cannot initialize video driver.

---

### Post by sojusnik on 2010-09-09
Hi there,

Found nothing useful after some research.

---

### Post by vbsaltydog on 2010-09-09
Then I would suggest better hardware.

---

