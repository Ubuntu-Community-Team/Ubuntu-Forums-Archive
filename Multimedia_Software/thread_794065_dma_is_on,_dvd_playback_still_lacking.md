---
title: "dma is on, dvd playback still lacking"
date: 2008-05-14
forum: Multimedia Software
---

### Post by miickEe on 2008-05-14
Hey

From what I can see in my hdparm.conf file, my drive has dma = on, and yet my video still seems to be unnaturally unwatchable. I watch music dvds by the way, and it's hard to explain but the video is just slow and painful to watch. I don't know what to do.

I've played around with video settings in vlc, and in movie player etc and it all doesn't work.

Suggestions (please)?

---

### Post by miickEe on 2008-05-14
My dvd rom is /dev/scd0, which means it is scsi from what I understand. Apparently hdparm does not work on scsi drives, so dma being enabled is not really an issue.

I've read that my xserver.xorg is configured wrong, and that I should run:
"sudo dpkg-reconfigure xserver-xorg"

And this is what I saw written in the same thread I obtained this info:
"Very good news! I'm able to play DVD.

and this was not a DMA issue!!!

In fact I have an ATI Radeon card and the DRI was not enabled. I removed all the fglrx drivers, re-installed the ATI driver as well as the restricted kernel module for ATI and it works!"

I have an nvidia geforce fx 5200, with the latest drivers etc. Where does my problem lie, what do I have to do to get my dvd video working correctly?

---

### Post by miickEe on 2008-05-14
Do I need to edit my /etc/modules file with anything? Is that needed for what I'm looking for?

I've heard it might be because speed from drive to system is slow, is there a way to tweak that?

And sdparm.. what is it, should I use it, will it be of any help?

---

### Post by miickEe on 2008-05-15
Here are some outputs from some commands

miickee@miickee-desktop:~$ sudo hdparm -Tt /dev/scd0

/dev/scd0:
 Timing cached reads:   630 MB in  2.00 seconds = 315.02 MB/sec
 Timing buffered disk reads:   10 MB in  3.51 seconds =   2.85 MB/sec

miickee@miickee-desktop:~$ sudo hdparm -I /dev/scd0

/dev/scd0:

ATAPI CD-ROM, with removable media
	Model Number:       PIONEER DVD-RW  DVR-115D                
	Serial Number:      GKDP265637WL       
	Firmware Revision:  1.13    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
Capabilities:
	LBA, IORDY(can be disabled)
	Buffer size: 64.0kB
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=240ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	Power Management feature set
	   *	PACKET command feature set
	   *	DEVICE_RESET command
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by the jumper

miickee@miickee-desktop:~$ sudo hdparm -i /dev/scd0

/dev/scd0:

 Model=PIONEER DVD-RW  DVR-115D                , FwRev=1.13    , SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=13395, BuffSize=64kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

Mean anything to you?

---

### Post by miickEe on 2008-05-16
B-U-M-P. I really need help with this.

---

### Post by miickEe on 2008-05-18
Bump. bump, bump.

I'm not kidding.

---

### Post by rbalfour on 2008-05-18
> **miickEe said:**
> Hey

From what I can see in my hdparm.conf file, my drive has dma = on, and yet my video still seems to be unnaturally unwatchable. I watch music dvds by the way, and it's hard to explain but the video is just slow and painful to watch. I don't know what to do.

I've played around with video settings in vlc, and in movie player etc and it all doesn't work.

Suggestions (please)?

Take one step back from the keyboard and take a deep breath.

Okay, you feel refreshed? Now let's get started.

1) this is either a video card conf issue or a faulty drive.
2) I will show you the tests, you run them. 

First let's test the video.


```
$ glxgears -info
```

Collect the following info.
[I]GL_RENDERER   = ???
GL_VERSION    = ???
GL_VENDOR     = ???
GL_EXTENSIONS = ???[/I]

At the bottom of the screen you should see something like this:
*2782 frames in 5.0 seconds = 552.702 FPS*

let it run for at **LEAST 5 lines**, collect that info.

Okay with that, do you have a XviD or Divx5 encoded file, the length should be at least 10 mins. Play that file and report back on quality. Does it lag? Does it should right? etc.

Next testing the drive.

Next test, put in a Audio CD and listen to it. Does the audio should good? Does the music skip?

And the finally test, put in a data CD. Anything with over 100MB, copy the contents of the data cd to a folder on your Hard Disk, you can delete what you copied. Does it copy correctly? How long did it take? etc.

---

### Post by miickEe on 2008-05-18
"miickee@miickee-desktop:~$ glxgears -info
GL_RENDERER   = GeForce FX 5200/AGP/SSE2/3DNOW!
GL_VERSION    = 2.1.2 NVIDIA 169.12
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_fragment_program GL_ARB_fragment_program_shadow GL_ARB_fragment_shader GL_ARB_half_float_pixel GL_ARB_imaging GL_ARB_multisample GL_ARB_multitexture GL_ARB_occlusion_query GL_ARB_pixel_buffer_object GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_shader_objects GL_ARB_shading_language_100 GL_ARB_texture_border_clamp GL_ARB_texture_compression GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_texture_rectangle GL_ARB_transpose_matrix GL_ARB_vertex_buffer_object GL_ARB_vertex_program GL_ARB_vertex_shader GL_ARB_window_pos GL_S3_s3tc GL_EXT_texture_env_add GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_compiled_vertex_array GL_EXT_Cg_shader GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_framebuffer_blit GL_EXT_framebuffer_multisample GL_EXT_framebuffer_object GL_EXT_gpu_program_parameters GL_EXT_multi_draw_arrays GL_EXT_packed_depth_stencil GL_EXT_packed_pixels GL_EXT_paletted_texture GL_EXT_pixel_buffer_object GL_EXT_point_parameters GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_shared_texture_palette GL_EXT_stencil_two_side GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_compression_s3tc GL_EXT_texture_cube_map GL_EXT_texture_edge_clamp GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_filter_anisotropic GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_texture_sRGB GL_EXT_timer_query GL_EXT_vertex_array GL_IBM_rasterpos_clip GL_IBM_texture_mirrored_repeat GL_KTX_buffer_region GL_NV_blend_square GL_NV_copy_depth_to_color GL_NV_depth_clamp GL_NV_fence GL_NV_float_buffer GL_NV_fog_distance GL_NV_fragment_program GL_NV_fragment_program_option GL_NV_framebuffer_multisample_coverage GL_NV_half_float GL_NV_light_max_exponent GL_NV_multisample_filter_hint GL_NV_occlusion_query GL_NV_packed_depth_stencil GL_NV_pixel_data_range GL_NV_point_sprite GL_NV_primitive_restart GL_NV_register_combiners GL_NV_register_combiners2 GL_NV_texgen_reflection GL_NV_texture_compression_vtc GL_NV_texture_env_combine4 GL_NV_texture_expand_normal GL_NV_texture_rectangle GL_NV_texture_shader GL_NV_texture_shader2 GL_NV_texture_shader3 GL_NV_vertex_array_range GL_NV_vertex_array_range2 GL_NV_vertex_program GL_NV_vertex_program1_1 GL_NV_vertex_program2 GL_NV_vertex_program2_option GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow GL_SUN_slice_accum 
3589 frames in 5.0 seconds = 717.164 FPS
3636 frames in 5.0 seconds = 727.123 FPS
3659 frames in 5.0 seconds = 731.761 FPS
3626 frames in 5.0 seconds = 725.076 FPS
3624 frames in 5.0 seconds = 724.704 FPS
3635 frames in 5.0 seconds = 726.882 FPS
3733 frames in 5.0 seconds = 746.512 FPS
3663 frames in 5.0 seconds = 732.562 FPS"

I played a 70MB xvid video file perfectly all the way through.

Audio cd works fine.

148.5MB of data copied to harddrive in around 2 minutes, copied correctly.

---

### Post by rbalfour on 2008-05-18
Okay the good news is. 1-You card is fine 2-the drive is fine. 
So now we are looking at a software issue.
To bypass any mis-understanding.
From console, run the following. and copy and paste the output BEFORE you press "Y".

$ apt-get install vlc vlc-plugin-*

I will be watching the forums for the next hour.

---

### Post by miickEe on 2008-05-18
"miickee@miickee-desktop:~$ sudo apt-get install vlc vlc-plugin-*
[sudo] password for miickee: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc is already the newest version.
Note, selecting vlc-plugin-dvb for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-ggi for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-esd for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-mad for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-alsa for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-ogg for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-sdl for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-arts for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-glide for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-xosd for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-svgalib for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-aa for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-pulse for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-dv for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-lirc for regex 'vlc-plugin-*'
Note, selecting vlc-plugin-a52 for regex 'vlc-plugin-*'
The following extra packages will be installed:
  libglide2 vlc-plugin-alsa vlc-plugin-arts vlc-plugin-esd vlc-plugin-ggi
  vlc-plugin-glide vlc-plugin-sdl vlc-plugin-svgalib
Suggested packages:
  device3dfx-module device3dfx-source
Recommended packages:
  glide2-bin
The following NEW packages will be installed:
  libglide2 vlc-plugin-alsa vlc-plugin-arts vlc-plugin-esd vlc-plugin-ggi
  vlc-plugin-glide vlc-plugin-sdl vlc-plugin-svgalib
0 upgraded, 8 newly installed, 0 to remove and 21 not upgraded.
Need to get 408kB of archives.
After this operation, 1278kB of additional disk space will be used.
Do you want to continue [Y/n]? "

I'd like o agree with you that it's a software issue but it doesn't take into account that this problem is not just within the scope of vlc but all media players, and the low disk read speeds.

---

### Post by rbalfour on 2008-05-18
Go ahead and press "Y". Once the install is done. try a dvd video.
If you have changed any default settings in VLC, put them back to default.

---

### Post by miickEe on 2008-05-18
I would play it in vlc if I could but it crashes when I start it up now lol, it was happening long before I installed these new plugins though. FUnnily enough, dvd is playing a lot better with the other media players, however that depends on what kind of dvd and whether it's in fullscreen or not.

---

### Post by rbalfour on 2008-05-18
> **miickEe said:**
> I would play it in vlc if I could but it crashes when I start it up now lol, it was happening long before I installed these new plugins though. FUnnily enough, dvd is playing a lot better with the other media players, however that depends on what kind of dvd and whether it's in fullscreen or not.

Go via the Package Manager and completely remove VLC.
Look at the attached screenshot. You will only need to do VLC.
Once that is done, reinstall VLC.
That should give you a fresh install to start from.

---

### Post by miickEe on 2008-05-18
It keeps crashing even after a complete removal and reinstallation.

---

### Post by rbalfour on 2008-05-18
From shell.

$ vlc -v

Please whatever it prints out.

---

### Post by miickEe on 2008-05-18
miickee@miickee-desktop:~$ vlc -v
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: DISASTERPIECES_1
libdvdnav: DVD Serial Number: c1584f68        
libdvdnav: DVD Title (Alternative): DISASTERPIECES_1
libdvdnav: Unable to find map file '/home/miickee/.dvdnav/DISASTERPIECES_1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00c00000. Regions: 1 2 3 4 5 6

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000146
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0002cc1f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000964a2
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
[00000350] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
[00000353] main private warning: dts != current_pts (181048)
[00000353] main private warning: backward_pts != current_pts (-40000)
[00000351] main audio output warning: PTS is out of range (158240), dropping buffer
[00000351] main audio output warning: PTS is out of range (126595), dropping buffer
[00000351] main audio output warning: PTS is out of range (94634), dropping buffer
[00000351] main audio output warning: PTS is out of range (62664), dropping buffer
[00000351] main audio output warning: PTS is out of range (30692), dropping buffer
[00000351] main audio output warning: PTS is out of range (-1281), dropping buffer
[00000351] main audio output warning: PTS is out of range (-33252), dropping buffer
[00000347] main video output warning: late picture skipped (185433)
[00000347] main video output warning: late picture skipped (145476)
[00000347] main video output warning: late picture skipped (65482)
[00000347] main video output warning: late picture skipped (25488)
[00000351] main audio output warning: computed PTS is out of range (8474), clearing out
[00000351] main audio output warning: PTS is out of range (8516), dropping buffer
[00000351] main audio output warning: output PTS is out of range (8524), clearing out
[00000351] main audio output warning: PTS is out of range (-23466), dropping buffer
[00000347] main video output warning: late picture skipped (29144)
[00000351] main audio output warning: PTS is out of range (-37205), dropping buffer
[00000347] main video output warning: late picture skipped (71868)
[00000347] main video output warning: late picture skipped (32174)
[00000347] main video output warning: late picture skipped (-7796)
[00000347] main video output warning: late picture skipped (19810)
[00000347] main video output warning: late picture skipped (-20081)
[00000377] main private warning: dts != current_pts (156552)
[00000377] main private warning: backward_pts != current_pts (-40000)
[00000380] main private warning: dts != current_pts (-18459)
[00000375] main video output warning: late picture skipped (149284)
[00000375] main video output warning: late picture skipped (109323)
[00000375] main video output warning: late picture skipped (69330)
[00000375] main video output warning: late picture skipped (69336)
[00000375] main video output warning: late picture skipped (69341)
[00000375] main video output warning: late picture skipped (73393)
[00000375] main video output warning: late picture skipped (94104)
[00000375] main video output warning: late picture skipped (185699)
[00000375] main video output warning: late picture skipped (269691)
[00000375] main video output warning: late picture skipped (350808)
[00000375] main video output warning: late picture skipped (431855)
[00000375] main video output warning: late picture skipped (512898)
[00000375] main video output warning: late picture skipped (593907)
[00000375] main video output warning: late picture skipped (674909)
[00000375] main video output warning: late picture skipped (755937)
[00000375] main video output warning: late picture skipped (837155)
[00000375] main video output warning: late picture skipped (918211)
[00000375] main video output warning: late picture skipped (999456)
[00000375] main video output warning: late picture skipped (1080256)
[00000383] main private warning: dts != current_pts (-19652)
[00000383] main private warning: backward_pts != current_pts (-40000)
[00000384] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:224000
[00000375] main video output warning: late picture skipped (51462)
[00000375] main video output warning: late picture skipped (11711)
[00000375] main video output warning: late picture skipped (-28250)
[00000375] main video output warning: late picture skipped (-14054)
[00000375] main video output warning: late picture skipped (-2736)
[00000375] main video output warning: late picture skipped (-42624)
[00000375] main video output warning: late picture skipped (-35142)
[00000375] main video output warning: late picture skipped (-30261)
[00000375] main video output warning: late picture skipped (-39563)
[00000375] main video output warning: late picture skipped (-46480)
[00000375] main video output warning: late picture skipped (-17771)
[00000375] main video output warning: late picture skipped (-18001)
[00000375] main video output warning: late picture skipped (-29925)
[00000375] main video output warning: late picture skipped (-5976)
[00000375] main video output warning: late picture skipped (-8193)
[00000375] main video output warning: late picture skipped (-15601)
[00000375] main video output warning: late picture skipped (-23691)
[00000375] main video output warning: late picture skipped (3752)
[00000375] main video output warning: late picture skipped (-36143)
[00000375] main video output warning: late picture skipped (12708)
[00000375] main video output warning: late picture skipped (55649)
[00000375] main video output warning: late picture skipped (15756)
[00000375] main video output warning: late picture skipped (-24216)
[00000375] main video output warning: late picture skipped (-27359)
[00000375] main video output warning: late picture skipped (-34345)
[00000375] main video output warning: late picture skipped (-33616)
[00000375] main video output warning: late picture skipped (-647)
[00000375] main video output warning: late picture skipped (187114)
[00000375] main video output warning: late picture skipped (147229)
[00000375] main video output warning: late picture skipped (107255)
[00000375] main video output warning: late picture skipped (67279)
[00000375] main video output warning: late picture skipped (27301)
[00000375] main video output warning: late picture skipped (67025)
[00000375] main video output warning: late picture skipped (27135)
[00000375] main video output warning: late picture skipped (-12838)
[00000375] main video output warning: late picture skipped (-24810)
[00000375] main video output warning: late picture skipped (-39627)
[00000375] main video output warning: late picture skipped (-46857)
[00000290] main playlist: stopping playback

---

### Post by miickEe on 2008-05-18
Ok the dvd playback is pixellated to the max, despite the fact the dvd is very good quality :S

---

### Post by zhuqing123 on 2008-05-18
The fourth [wow power leveling](http://www.wow-powerleveling.org) latest game in [wow power leveling](http://www.xowow.com) Warcraft series is ‘[wow power leveling](http://www.powerlevelingweb.com)’. Also known as [wow power leveling](http://www.igsstar.com), it represents a [wow power leveling](http://www.wowgoldweb.com) multiplayer online [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) game, the best of [wow power leveling](http://www.powerleveling-wow.com) kind. Initially, it was [wow gold](http://www.wow-powerleveling.org) it be released in 2001, but [wow powerleveling](http://www.powerleveling-wow.com) was delayed [wow powerleveling](http://www.powerlevelingweb.com) 2004, thus [wow powerleveling](http://www.xowow.com) the 10 years of[wow powerleveling](http://www.wow-powerleveling.org) franchise of this[wow gold](http://www.xowow.com) series. The [world of warcraft power leveling](http://www.powerlevelingweb.com) was not [world of warcraft power leveling](http://www.wow-powerleveling.org/wow+power+leveling.html)fulfilling, because [wow power level](http://www.powerleveling-wow.com/siteMap.asp)problems with [wow power level](http://www.powerlevelingweb.com) server’s stability [power leveling wow](http://www.powerleveling-wow.com/siteMap.asp) performance occurred, but [power leveling wow](http://www.xowow.com) game still [power leveling wow](http://www.powerlevelingweb.com) a financial success [powerleveling wow](http://www.powerleveling-wow.com/siteMap.asp) the most [powerleveling wow](http://www.xowow.com) game of its kind. The number [cheap wow power leveling ](http://www.powerlevelingweb.com) users that play [Maple Story mesos](http://www.igsstar.com/Maple-Story-mesos-us/), exceeds 8.5 [MapleStory mesos](http://www.igsstar.com/Maple-Story-mesos-us/), worldwide.As a form [ms mesos](http://www.igsstar.com/Maple-Story-mesos-us/),recognition for [mesos](http://www.igsstar.com/Maple-Story-mesos-us/),outstanding popularity, the game [SilkRoad Gold](http://www.igsstar.com/Silkroad-Online-Gold/), received a[SRO Gold](http://www.igsstar.com/Silkroad-Online-Gold/), of awards. Now the question [eq2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), why is [eq2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), game [eq2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), popular? For anyone[EverQuest 2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), played the previous [EverQuest 2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), and [EverQuest 2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), already initiated [lotro gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the mysterious world [lotr gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the breathtaking [Lord of the Rings online Gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), this [Rolex Replica](http://www.watchreplicashop.com/) nothing but an [Replica Rolex](http://www.watchreplicashop.com/) adventure that continues the story of ‘Warcraft III: Frozen Throne’, four years after conclusion, in the world of Azeroth. The game is online role-playing, the previous versions being online and offline strategy games. The major thrills and unique features are present as in every Blizzard game.

---

### Post by rbalfour on 2008-05-18
I am sure you have done this. But you can you run this command.
$ sudo /usr/share/doc/libdvdread3/install-css.sh

and post the output. Also, it's a bit late in the game. What version of Ubuntu are you on? Your libdvdcss is reporting 1.2.9 - the repo is only 1.2.5
Also have you ROM "burn" the dvd drive, ie changed the firmware of the DVD/CD drive?

---

### Post by miickEe on 2008-05-18
miickee@miickee-desktop:~$ sudo /usr/share/doc/libdvdread3/install-css.sh
[sudo] password for miickee: 
--12:12:19--  [http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb](http://www.dtek.chalmers.se/groups/dvd/deb/libdvdcss2_1.2.5-1_i386.deb)
           => `/tmp/dvdcss-CR6346/libdvdcss.deb'
Resolving [www.dtek.chalmers.se](www.dtek.chalmers.se)... 129.16.30.198
Connecting to [www.dtek.chalmers.se|129.16.30.198|:80](www.dtek.chalmers.se|129.16.30.198|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 25,178 (25K) [text/plain]

100%[====================================>] 25,178        17.11K/s             

12:12:21 (17.08 KB/s) - `/tmp/dvdcss-CR6346/libdvdcss.deb' saved [25178/25178]

dpkg - warning: downgrading libdvdcss2 from 1.2.9-2medibuntu4 to 1.2.5-1.
(Reading database ... 119620 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.9-2medibuntu4 (using .../dvdcss-CR6346/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.5-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Ubuntu 8.04 is the version I'm residing on.
miickee@miickee-desktop:~$ uname -a
Linux miickee-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

No I haven't changed the firmware for my dvd drive

---

### Post by rbalfour on 2008-05-18
Not sure how you did it. But you have Ubuntu Studio CSS.
**1.2.9-2medibuntu4**

Reboot. test 1-a reg movie dvd 2- the dvd that is giving you the problem.

---

### Post by mc4man on 2008-05-18
> 148.5MB of data copied to harddrive in around 2 minutes, that is not a good time, normally about 15 sec. Maybe the disk is damaged or your drive or related hardware is struggling.
> downgrading libdvdcss2 from 1.2.9-2medibuntu4 that is the correct medibuntu version for hardy 32 bit
> [00000353] main private warning: dts != current_pts (18104
[00000353] main private warning: backward_pts != current_pts (-40000)
[00000351] main audio output warning: PTS is out of range (158240), dropping buffer here's a short description ```

The DTS (Decoding Time Stamp) and PTS (Presentation Time Stamp) timestamps are when
the decoder is supposed to decode and display the frame relative to the SCR (System Clock
Reference) timestamp. The SCR can be thought of as the time the decoder is supposed to read
the data from the disk.
Every packet of data in the mpeg file has an SCR timestamp and this timestamp is the value
the system clock should be at when the packet is read. Usually, a decoder will start the system
clock when it starts reading an mpeg stream (the initial value of the system clock is the SCR
from the first packet of data, usually zero but it does not have to start at zero).
The DTS timestamp tells the decoder to decode the frame when the SCR time reaches the
DTS time, likewise for the PTS timestamp. Usually, the DTS/PTS timestamps indicate a time
later than the SCR of the packet the video/audio appear in. For example, if the SCR of a
packet of video data is 100ms (meaning it is read from the disk 100ms after the start of
playback), the DTS/PTS values would be something like 200/280ms, meaning when the SCR
reaches 200ms this video data is supposed to be decoded and then 80ms later it is to be
displayed (the video data is held in a buffer until decoding time) 
```  all in all it seems to be pointing to a hardware issue
you could try using a player that lets you set a high cache, or a fresh install of vlc, dvdnav, dvdread, the Os, ect. It may be more useful if you could try a different dvd drive, maybe borrow one. No sense buying if issue is elsewhere

---

### Post by miickEe on 2008-05-19
Dvd still very bad quality, which I know it isn't. Sorry, had to resize a partition and then my sound drivers and flash decided to screw up on me again so I had to fix that up.

Actually, the quality has improved but not to (dare I say it) the standard that I got while using windows. I know it's nitpicking now but hmm.. Thanks for the in-depth help by the way mate.

---

### Post by miickEe on 2008-05-19
Ok pretty much back to square one, just all turned to crap now.

I've put another dvd drive in there, still gets the slow read speeds.

Video playback is unreliable and very sensitive to scenes with a lot of movement. It's very pixellated, so maybe it can't get enough information from the disc in the time it needs and needs to pad it?

I have no other options, do I? I mean, could it also be a video card issue?
[EDIT]
I have ogle and it works a complete charm for some dvds, the rest are "liney" (look too digital, don't ask me that's the best description I can give lol).

---

