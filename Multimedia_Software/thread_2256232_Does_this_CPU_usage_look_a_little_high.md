---
title: "Does this CPU usage look a little high?"
date: 2014-12-10
forum: Multimedia Software
---

### Post by SagaciousKJB on 2014-12-10
[[IMG]http://i1266.photobucket.com/albums/jj528/sagaciouskjb/Screenshot-12102014-024435PM.png[/IMG]](http://s1266.photobucket.com/user/sagaciouskjb/media/Screenshot-12102014-024435PM.png.html)

It seems like it's taking up a lot of my CPU just to play mplayer and run Chromium with 2 tabs open.  It's just standard def video...

```
Format                                   : Matroska
Format version                           : Version 2
File size                                : 277 MiB
Duration                                 : 23mn 27s
Overall bit rate                         : 1 650 Kbps
Encoded date                             : UTC 2009-08-07 03:06:20
Writing application                      : mkvmerge v2.9.7 ('Tenderness') built on Jul  1 2009 18:43:35
Writing library                          : libebml v0.7.7 + libmatroska v0.8.1

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L4.1
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 8 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 23mn 27s
Bit rate                                 : 1 200 Kbps
Width                                    : 720 pixels
Height                                   : 480 pixels
Display aspect ratio                     : 4:3
Frame rate                               : 23.976 fps
Standard                                 : NTSC
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.145
Stream size                              : 196 MiB (71%)
Writing library                          : x264 core 68 r1183M f21daff
Encoding settings                        : cabac=1 / ref=8 / deblock=1:-3:-3 / analyse=0x3:0x113 / me=esa / subme=9 / psy_rd=1.0:0.3 / mixed_ref=1 / me_range=32 / chroma_me=1 / trellis=2 / 8x8dct=1 / cqm=0 / deadzone=21,11 / chroma_qp_offset=-4 / threads=12 / nr=0 / decimate=0 / mbaff=0 / bframes=5 / b_pyramid=0 / b_adapt=2 / b_bias=0 / direct=3 / wpredb=1 / keyint=250 / keyint_min=25 / scenecut=40 / rc=2pass / bitrate=1200 / ratetol=1.0 / qcomp=0.60 / qpmin=10 / qpmax=51 / qpstep=4 / cplxblur=20.0 / qblur=0.5 / vbv_maxrate=17500 / vbv_bufsize=14000 / ip_ratio=1.40 / pb_ratio=1.30 / aq=1:1.00
Language                                 : English
Default                                  : Yes
Forced                                   : No

Audio
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : A_AC3
Duration                                 : 23mn 27s
Bit rate mode                            : Constant
Bit rate                                 : 448 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 75.2 MiB (27%)
Language                                 : English
Default                                  : Yes
Forced                                   : No
```

I've tried a bunch of different video output modules too and they're all about the same.

And that's just leaving it basically idle, once I start loading up different web pages--especially flash--the CPU loads up right away.

---

### Post by ibjsb4 on 2014-12-11
What does top say?
```
top
```
What kind of processor is this?

---

### Post by SagaciousKJB on 2014-12-11
The bottom portion of my conky configuration is top output.

It's an AMD Turion X2 RM-70.  Dual core 2 ghz

Heres the output of the actual top program

```
Tasks: 183 total,   2 running, 179 sleeping,   0 stopped,   2 zombie
Cpu(s): 28.8%us,  5.9%sy,  0.6%ni, 64.2%id,  0.3%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2824476k total,  2328280k used,   496196k free,    29896k buffers
Swap:        0k total,        0k used,        0k free,  1344716k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9281 kenny     20   0  622m  71m  38m S   29  2.6 393:30.46 mplayer            
 1184 root      20   0  410m 215m 125m S   15  7.8 354:58.75 Xorg               
 2173 kenny      9 -11  408m 6308 4240 S    8  0.2 134:29.01 pulseaudio         
 2382 kenny     20   0  250m  27m  12m R    4  1.0  26:33.31 xchat              
 2390 kenny     20   0  254m  14m  10m S    4  0.5  57:18.45 xfce4-terminal     
23875 kenny     20   0 17332 1300  908 R    4  0.0   0:00.02 top                
 2122 kenny     20   0  156m  13m 9364 S    2  0.5  26:22.94 xfwm4              
23844 root      20   0     0    0    0 S    2  0.0   0:00.84 kworker/0:2        
    1 root      20   0 24600 2484 1240 S    0  0.1   0:01.23 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.10 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:08.62 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:01.35 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.04 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:07.58 ksoftirqd/1        
   12 root      RT   0     0    0    0 S    0  0.0   0:01.10 watchdog/1         
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset 
```

---

### Post by ibjsb4 on 2014-12-12
Thanks for the top output, easier for a non-conky person :)

Your xorg runs high, what video drivers have you tried?

Do you have video compositing enabled?

Edit:
An afterthought, can you log into a guest account and check usage?

---

### Post by Yellow Pasque on 2014-12-12
So that top output is while playing video? It doesn't look high at all to me, especially for a Turion.

What kind of video card/driver are you using and what mplayer output are you using?

---

### Post by SagaciousKJB on 2014-12-12
I'm not sure about video composting, don't know what that is.

I'm using the gl driver because that one had benchmarked better before, but usually it's neck and neck with xv.  This time xv was a little better.  The second line is the CPU usage.

```
VO: [gl] 640x480 => 640x480 Planar YV12  [fs]
A:   3.0 V:   3.0 A-V: -0.001 ct:  0.125   0/  0 21%  5%  1.1% 2 0 


BENCHMARKs: VC:   0.689s VO:   0.190s A:   0.035s Sys:   2.143s =    3.056s
BENCHMARK%: VC: 22.5298% VO:  6.2141% A:  1.1514% Sys: 70.1047% = 100.0000%
BENCHMARKn: disp: 74 (24.21 fps)  drop: 2 (2%)  total: 76 (24.87 fps)
```

xv was second best

```
VO: [xv] 640x480 => 640x480 Planar YV12  [fs]
A:   2.8 V:   2.8 A-V:  0.001 ct:  0.041   0/  0 17%  3%  1.3% 0 0 


BENCHMARKs: VC:   0.476s VO:   0.084s A:   0.036s Sys:   2.161s =    2.757s
BENCHMARK%: VC: 17.2618% VO:  3.0417% A:  1.3098% Sys: 78.3867% = 100.0000%
BENCHMARKn: disp: 69 (25.03 fps)  drop: 0 (0%)  total: 69 (25.03 fps)
```

The video card is a Radeon HD 3100 Mobile with fglrx.  Had to use an older version of fglrx though because they moved support for my card to legacy drivers on the last update.

I'll see what happens in a guest account

Edit:

The guest account didn't seem to make any difference.

Edit:
Temüjin yeah that was while it was playing.  I tried on my desktop, it has a Phenom 9950, and it only used like 7% of the CPU.  I guess the Turion just isn't fast enough even at 2 ghz?

---

### Post by Rob Sayer on 2014-12-13
Video compositing means eye candy.  There's a setting for that in xfce.  I don't remember exactly because I don't use xfce anymore.  I think it's in window manager tweaks.  I'd make sure it's turned off.

---

### Post by Yellow Pasque on 2014-12-13
> **Rob Sayer said:**
> Video compositing means eye candy.

There's more to it than that. xfce's compositor is pretty basic and doesn't have a lot of demanding animation. 

> I'd make sure it's turned off. 

That's great until your video starts tearing...
If xfce's compositor is causing significant CPU usage, then I'd try compton before trying to get rid of compositing altogether. (Actually, I use xfce+compton on my main install).

---

### Post by Yellow Pasque on 2014-12-13
> The video card is a Radeon HD 3100 Mobile with fglrx. Had to use an older version of fglrx though because they moved support for my card to legacy drivers on the last update.

What version of Ubuntu are you running? Unless it's 12.04.1 or older, you're probably not using fglrx-legacy since it doesn't work with modern kernels and X servers.
Give output of:
```
glxinfo
```
If you can copy/paste /var/log/Xorg.0.log (into code blocks, of course), that might be helpful too.

>  I tried on my desktop, it has a Phenom 9950, and it only used like 7% of the CPU. 
Well, the 9950 is a newer, quad core chip running at a faster clock speed and it's possible you're offloading some of the video decoding to the GPU on the Phenom system depending on what kind of GPU it has and what driver it's using. So, yes, lower CPU usage on the Phenom system is expected.

> I guess the Turion just isn't fast enough even at 2 ghz?
I'm not sure what "fast enough" is referring to. Is the video stuttering or something? It seems like you expect to watch video without so much as throttling your CPU. That's unrealistic.
The bottom line is that the Turion is certainly not the most powerful/efficient chip to use for video playback, especially if you don't have any kind of video decoding being offloaded. I think that brings us to the crux of your issue...

If you're using the open-source radeon driver with a RadeonHD 2000-3000 GPU, it does not offload video decoding using VDPAU. That feature has only very been recently enabled by AMD: [http://www.phoronix.com/scan.php?page=news_item&px=MTc3MTc](http://www.phoronix.com/scan.php?page=news_item&px=MTc3MTc)
If you want to try that feature, you would need a 3.18 kernel, a newer version of mesa, and some firmware files extracted to /lib/firmware/radeon [http://people.freedesktop.org/~agd5f/radeon_ucode/uvd-firmware-old-chips.tar.gz](http://people.freedesktop.org/~agd5f/radeon_ucode/uvd-firmware-old-chips.tar.gz)

---

### Post by SagaciousKJB on 2014-12-13
> **Temüjin said:**
> What version of Ubuntu are you running? Unless it's 12.04.1 or older, you're probably not using fglrx-legacy since it doesn't work with modern kernels and X servers.
Give output of:
```
glxinfo
```
If you can copy/paste /var/log/Xorg.0.log (into code blocks, of course), that might be helpful too.

 
Well, the 9950 is a newer, quad core chip running at a faster clock speed and it's possible you're offloading some of the video decoding to the GPU on the Phenom system depending on what kind of GPU it has and what driver it's using. So, yes, lower CPU usage on the Phenom system is expected.


I'm not sure what "fast enough" is referring to. Is the video stuttering or something? It seems like you expect to watch video without so much as throttling your CPU. That's unrealistic.
The bottom line is that the Turion is certainly not the most powerful/efficient chip to use for video playback, especially if you don't have any kind of video decoding being offloaded. I think that brings us to the crux of your issue...

If you're using the open-source radeon driver with a RadeonHD 2000-3000 GPU, it does not offload video decoding using VDPAU. That feature has only very been recently enabled by AMD: [http://www.phoronix.com/scan.php?page=news_item&px=MTc3MTc](http://www.phoronix.com/scan.php?page=news_item&px=MTc3MTc)
If you want to try that feature, you would need a 3.18 kernel, a newer version of mesa, and some firmware files extracted to /lib/firmware/radeon [http://people.freedesktop.org/~agd5f/radeon_ucode/uvd-firmware-old-chips.tar.gz](http://people.freedesktop.org/~agd5f/radeon_ucode/uvd-firmware-old-chips.tar.gz)

It's 12.04.4 but by the legacy driver I don't mean the legacy package offered by Ubuntu, I mean AMD moved my card to legacy support.  So I had to install fglrx=2:8.960 because the newer one in 2:13.350 doesn't support my card any more.

Should I post the whole output of glxinfo?  It's quite large.

I'm using the proprietary ATI driver because the radeon one underscanned on my TV and displayed some weird green borders.

What type of CPU throttling should I try? Renicing the mplayer process?  The problem is that when I try to browse webpages at the same time, the CPU load goes up to 100% and makes the video lose A/V sync

---

### Post by Yellow Pasque on 2014-12-14
Just the first 50 lines or so should do:
```
uname -a
glxinfo |  head -n 50
```

> What type of CPU throttling should I try?
I think you misunderstood what I was trying to say there. Nevermind.

> I'm using the proprietary ATI driver
You won't be able to offload any video decoding to your GPU using that.

---

### Post by SagaciousKJB on 2014-12-14
```
kenny@laptop:~$ uname -a
Linux laptop 3.2.0-74-generic #109-Ubuntu SMP Tue Dec 9 16:45:49 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
kenny@laptop:~$ glxinfo | head -n 50
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: ATI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group
client glx vendor string: ATI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_allocate_memory, GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap, GLX_EXT_framebuffer_sRGB, 
    GLX_ARB_fbconfig_float, GLX_AMD_gpu_association
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile, 
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_swap_control, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_MESA_swap_control, GLX_NV_swap_group, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_swap_barrier, GLX_SGIX_swap_group, GLX_SGIX_visual_select_group, 
    GLX_EXT_texture_from_pixmap
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: ATI Radeon 3100 Graphics 
OpenGL version string: 3.3.11627 Compatibility Profile Context
OpenGL shading language version string: 3.30
OpenGL extensions:
    GL_AMDX_debug_output, GL_AMD_conservative_depth, GL_AMD_debug_output, 
    GL_AMD_depth_clamp_separate, GL_AMD_draw_buffers_blend, 
    GL_AMD_name_gen_delete, GL_AMD_performance_monitor, GL_AMD_pinned_memory, 
    GL_AMD_sample_positions, GL_AMD_shader_stencil_export, 
    GL_ARB_ES2_compatibility, GL_ARB_base_instance, 
    GL_ARB_blend_func_extended, GL_ARB_color_buffer_float, 
    GL_ARB_compressed_texture_pixel_storage, GL_ARB_conservative_depth, 
    GL_ARB_copy_buffer, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp, 
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend, 
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced, 
    GL_ARB_explicit_attrib_location, GL_ARB_fragment_coord_conventions, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 

```

That's too bad about not being able to offload any with the ATI driver, I hate the underscanning with the radeon driver.

---

### Post by Yellow Pasque on 2014-12-14
Oh, okay, you do have fglrx properly installed (I was a bit skeptical).

> That's too bad about not being able to offload any with the ATI driver, I hate the underscanning with the radeon driver. 

Have you tried anything more recent than Ubuntu 12.04.x? It's possible that the issues with the open source driver have been fixed in later versions. I'm not saying you should overwrite your current install, but it's worth a shot throwing the latest version of Ubuntu on a USB stick (I'd try a 15.04 image myself).

---

### Post by SagaciousKJB on 2014-12-14
Yeah, I tried Ubuntu 14.04 but I'm not sure I remember trying the opensource driver there.  I just know that the update fglrx they used no longer supported my card...  But anyway, are the open-source drivers packaged into the Live CDs?  It would be convenient if I could test them without having to install.

---

### Post by Yellow Pasque on 2014-12-14
Yes, the open source radeon driver is used by default on the Live media.

---

