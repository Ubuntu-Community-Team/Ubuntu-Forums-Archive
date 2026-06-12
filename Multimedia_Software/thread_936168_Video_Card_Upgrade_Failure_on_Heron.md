---
title: "Video Card Upgrade Failure on Heron"
date: 2008-10-02
forum: Multimedia Software
---

### Post by ofb on 2008-10-02
Upgraded a machine from Geforce4 MX 440SE to FX 5200. UT2004 crashes on load-up, Google Earth crashes on load-up, GL-117 crashes on load & locks the machine.

Otherwise it's fine. After the physical install, Ubuntu booted without Nvidia, then gave me the Restricted Driver dialog. I used that to take care of switching from nvidia-glx to nvidia-glx-new.

Have tried reinstalling the driver. Have dug through terminal output and logfiles without finding anything sensible to me. Haven't found anything with searches yet.

Next is probably a system reinstall, but I'm reluctant because that's a bit of a job and we're so close to Ibex.

The card is from a Fawn machine where there were no troubles, and the Windows partition has had no trouble with the upgrade. 

Some outputs:

```

o@redfish:~$ sh ut2004
Error loading JB-SpaceLego !
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
Signal: SIGILL [illegal instruction]
Aborting.


Crash information will be saved to your logfile.

```

```

Log: Log file open, Thu Oct  2 10:27:56 2008
Init: Name subsystem initialized
Init: Version: 3369 (128.29)
Init: Compiled: Dec 16 2005 13:23:47
Init: Command line: 
Init: (This is Linux patch version 3369.2)
Init: Character set: Unicode
Init: Base directory: /home/o/Thorax/games/ut2004/System/
Init: Ini:UT2004.ini   UserIni:User.ini
Init: Build label: UT2004 Build UT2004_Build_[2005-11-23_16.22]
Init: Object subsystem initialized
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 17.986339...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NoIntro.ut2?Name=Player?Class=Engine.Pawn?Character=soria?team=255?Sex=F?Voice=ZimGir2K4.ZimGir2K4?SpectatorOnly=1
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33582->33579; refs: 346838
Log: Game class is 'CinematicGame'
Log: Bringing Level NoIntro.myLevel up for play (0) appSeconds: 19.783956...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Warning: Failed to load 'JBToolbox': Can't find file for package 'JBToolbox'
Warning: Failed to load 'JB-SpaceLego': Can't find file for package 'JBToolbox'
Warning: Failed to load 'LevelSummary JB-SpaceLego.LevelSummary': Can't find file for package 'JBToolbox'
Warning: Error loading JB-SpaceLego !
Log: ALAudio: Using ALC_EXT_capture to record audio.
ScriptLog: New Player Player id=1fff90984cd534db710e82a37a01fbcd
Log: TTS: No output filename specified.
Log: Enter SetRes: 800x600 Fullscreen 1
Log: OpenGL
Log: GL_VENDOR     : NVIDIA Corporation
Log: GL_RENDERER   : GeForce FX 5200/AGP/3DNOW!
Log: GL_VERSION    : 2.1.2 NVIDIA 169.12
Log: OpenGL: Device supports: GL
Log: OpenGL: Device supports: GL_EXT_bgra
Log: OpenGL: Device supports: GL_ARB_texture_compression
Log: OpenGL: Device supports: GL_EXT_texture_compression_s3tc
Log: OpenGL: Device supports: GL_ARB_texture_cube_map
Log: OpenGL: Device supports: GL_ARB_texture_env_combine
Log: OpenGL: Device supports: GL_NV_texture_env_combine4
Log: OpenGL: Device supports: GL_EXT_texture_lod_bias
Log: OpenGL: Device supports: GL_ARB_multitexture
Log: OpenGL: Device supports: GL_NV_vertex_array_range
Log: OpenGL: Device supports: GL_NV_vertex_array_range2
Log: OpenGL: Device supports: GL_ARB_multisample
Log: OpenGL: Device supports: GL_NV_multisample_filter_hint
Log: OpenGL: Device supports: GL_EXT_texture_filter_anisotropic
Log: OpenGL: Device supports: GL_ARB_vertex_buffer_object
Log: OpenGL: Device supports: GL_ARB_fragment_program
Log: OpenGL: Device supports: GL_ARB_vertex_program
Log: OpenGL: Device supports: GL_EXT_framebuffer_object
Log: OpenGL: C32 RGB888 Z24 S0
Log: OpenGL: Level of anisotropy is 1.000000 (max 8.000000).
Log: OpenGL: Have 0 multisamples buffers, 0 samples.
Log: OpenGL: Failed to get a multisample GL context
Log: OpenGL: Forcibly disabled pixel shaders.
Log: OpenGL: Forcibly disabled render-to-texture.
Log: OpenGL: allocated 21 MByte of AGP memory
Log: Startup time: 29.806609 seconds
Log: Precaching: NoIntro.LevelInfo0
Log: Static mesh batches: 0 vertex bytes, 0 index bytes
Log: 
Developer Backtrace:
Log: [ 1]  ./ut2004-bin [0x874bdd9]
Log: [ 2]  [0xb7fbd420]
Log: [ 3]  /usr/lib/libGLcore.so.1 [0xb3571350]
Log: Unreal Call Stack: FOpenGLTexture::Cache <- FOpenGLRenderInterface::CacheTexture <- FOpenGLRenderInterface::HandleCombinedMaterial <- FOpenGLRenderInterface::SetSimpleMaterial <- FOpenGLRenderInterface::SetMaterial <- FBspDrawList::Render <- RenderLevel <- FLevelSceneNode::Render <- FPlayerSceneNode::Render <- UGameEngine::Draw <- USDLViewport::Repaint <- USDLClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop
Exit: Exiting.
Log: FileManager: Reading 0 GByte 39 MByte 616 KByte 434 Bytes from HD took 12.429169 seconds (12.429169 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Allocation checking disabled
Uninitialized: Log file closed, Thu Oct  2 10:28:28 2008

```

```

o@redfish:~$ googleearth
Google Earth has caught signal 4.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin [0x804f403]
  /usr/lib/googleearth/googleearth-bin [0x804f916]
  [0xb7f43420]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/o/.googleearth/crashlogs/crashlog-F2A68E96.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

```

```

CRASHLOGVER 1
CRASHLOGID 0xF2A68E96
APPVERMAJOR 4
APPVERMINOR 3
APPVERBUILD 7204
APPBUILDDATE Apr 24 2008
APPBUILDTIME 13:27:30
OSTYPE 11
OSVERMAJOR 2
OSVERMINOR 6
OSVERBUILD 24
OSVERPATCH 0
PID 7303
CRASHSIGNAL 4
CRASHTIME 1222968665
PROGRAMUPTIME 32

STACK 0x804f403
STACK 0x804f916
STACK 0xb7f43420

DSO googleearth-bin/0x8048000/45848
DSO googleearth-bin/0xb7f43000/1600
DSO libgcc_s.so.1/0xb7f36000/39096
DSO libstdc++.so.6/0xb7e5c000/849472
DSO libQtCore.so.4/0xb7c9e000/1791040
DSO libQtGui.so.4/0xb766e000/6344256
DSO libQt3Support.so.4/0xb7437000/2256436
DSO libQtNetwork.so.4/0xb73b1000/532172
DSO libQtXml.so.4/0xb7362000/314624
DSO libQtSql.so.4/0xb733a000/157044
DSO libgoogleearth_lib.so/0xb7247000/958561
DSO libm.so.6/0xb7211000/143140
DSO libc.so.6/0xb70c1000/1346856
DSO libpthread.so.0/0xb70a9000/80644
DSO libbase.so/0xb701f000/541908
DSO libge_net.so/0xb6feb000/203856
DSO libgeobase.so/0xb6cb7000/3255429
DSO libz.so.1/0xb6c9f000/86972
DSO libgthread-2.0.so.0/0xb6c9a000/12444
DSO librt.so.1/0xb6c91000/27472
DSO libglib-2.0.so.0/0xb6be0000/719692
DSO libdl.so.2/0xb6bdc000/7420
DSO libfreetype.so.6/0xb6b6e000/433892
DSO libSM.so.6/0xb6b66000/26384
DSO libICE.so.6/0xb6b4e000/83208
DSO libXi.so.6/0xb6b46000/27668
DSO libXrender.so.1/0xb6b3e000/28152
DSO libXrandr.so.2/0xb6b38000/20100
DSO libXfixes.so.3/0xb6b32000/12628
DSO libXcursor.so.1/0xb6b29000/31268
DSO libXinerama.so.1/0xb6b26000/4752
DSO libXext.so.6/0xb6b18000/51440
DSO libX11.so.6/0xb6a31000/933472
DSO libIGCore.so/0xb6940000/925528
DSO libapiloader.so/0xb693c000/9288
DSO libauth.so/0xb68ea000/322188
DSO libport.so/0xb68e6000/11612
DSO libcommon.so/0xb6820000/779064
DSO libcomponentframework.so/0xb6819000/19224
DSO libmath.so/0xb67f8000/128372
DSO libmoduleframework.so/0xb67ee000/35636
DSO librender.so/0xb67b3000/231725
DSO ld-linux.so.2/0xb7f44000/104496
DSO libIGUtils.so/0xb678d000/140876
DSO libIGMath.so/0xb6744000/271892
DSO libminizip.so/0xb673d000/21784
DSO libfusioncommon.so/0xb6739000/11220
DSO libcurl.so.4/0xb6706000/201204
DSO libpcre.so.3/0xb66df000/155300
DSO libXau.so.6/0xb66db000/5460
DSO libxcb-xlib.so.0/0xb66d9000/2636
DSO libxcb.so.1/0xb66c1000/91992
DSO libGL.so.1/0xb661d000/554694
DSO libGL.so.1/0xb66a56e0/112416
DSO libGLU.so.1/0xb659f000/507779
DSO libfreeimage.so.3/0xb64db000/770245
DSO libjpeg.so.62/0xb64b7000/139688
DSO libmng.so.1/0xb645a000/364312
DSO libpng12.so.0/0xb6432000/156964
DSO libtiff.so.3/0xb63d6000/364328
DSO libXdmcp.so.6/0xb63d0000/15076
DSO libGLcore.so.1/0xb58bb000/11352191
DSO libGLcore.so.1/0xb638f880/263092
DSO libnvidia-tls.so.1/0xb58b9000/1328
DSO libnss_compat.so.2/0xb4b15000/25532
DSO libnsl.so.1/0xb4afd000/79840
DSO libnss_nis.so.2/0xb4af3000/32200
DSO libnss_files.so.2/0xb4ae8000/35744
DSO libqjpeg.so/0xb4b25000/29240
DSO libIGGfx.so/0xb322e000/704344
DSO libevll.so/0xb2d12000/5200388
DSO libIGAttrs.so/0xb2cb0000/366572
DSO libIGSg.so/0xb2ba3000/1032004
DSO libalchemyext.so/0xb4b21000/11076
DSO libicuuc.so.38/0xb2a31000/1052797
DSO libnss_mdns4_minimal.so.2/0xb2a1d000/5908
DSO libnss_dns.so.2/0xb2a17000/15000
DSO libresolv.so.2/0xb2a04000/60744
DSO libcollada.so/0xb29c3000/256949
DSO libIGExportCommon.so/0xb293d000/510420
DSO libIGOpt.so/0xb2867000/820920
DSO libIGDisplay.so/0xb2854000/68604
DSO libIGGui.so/0xb2814000/238548
DSO libcollada-1.4.so/0xb2519000/3016032
DSO libqgif.so/0xb2a2b000/17104
DSO libnavigate.so/0xb0409000/1079193
DSO liblayer.so/0xb0281000/1561233
DSO libwmsbase.so/0xb021f000/387774
DSO libmeasure.so/0xb012b000/382508
DSO libbasicingest.so/0xb4b1f000/2500
DSO libgps.so/0xadf7e000/498415
DSO libgooglesearch.so/0xadf10000/433644
DSO libinput_plugin.so/0xb01fc000/134315
DSO libflightsim.so/0xada48000/777181

```

---

### Post by ofb on 2008-10-03
Right, seven hours later... I tried installing Ibex beta several times but kept having display failures during install. I'll add that to the bug reports tomorrow. I've just finished setting up a fresh install of Heron, and Google Earth fails just like before.

So, Heron does not like this FX 5200 for launching Google Earth and games. What do I look at next?

---

### Post by ofb on 2008-10-03
I just tried Envy as an experiment.
[http://ubuntuforums.org/showpost.php?p=5170207&postcount=16](http://ubuntuforums.org/showpost.php?p=5170207&postcount=16)

```

o@redfish:~$ googleearth
NVIDIA OpenGL Driver requires CPUs with SSE to run.

The current CPU does not support SSE.


o@redfish:~$ sh ut2004
NVIDIA OpenGL Driver requires CPUs with SSE to run.

The current CPU does not support SSE.
Signal: SIGSEGV [segmentation fault]
Aborting.


Crash information will be saved to your logfile.

```

---

### Post by ofb on 2008-10-04
After much reading I have some idea there's a problem with Nvidia drivers & CPUs without SSE, and possibly without SSE2 support*. Looks like P3+ has SSE, but with AMD some Duron and Athlon don't.

You can run 'grep -o sse /proc/cpuinfo' to see if that returns anything. Nothing returned means no SSE.

Looks like the problem may get thicker as of kernel 2.6.25. Something about it using only newer Nvidia drivers, and Nvidia dropping support for non-SSE CPU with its new driver releases.

Part of what's weird here is my older 440SE works fine on Heron, using 2.6.24-21 anyway. Possibly the nvidia-glx hasn't been updated recently. I rather hope it never is.

I couldn't install the Ibex beta (2.6.27) using the 440SE -- display failures during install again. But I don't know that that's related because the restricted Nvidia driver won't be installed until after first boot.

I do wish our LiveCDs would run some sort of hardware detect to tell people there's no point proceeding though. Seems between 'lshw' and 'grep sse' that would be simple.


* I'm not sure SSE2 has anything to do with running 3d. Perhaps the lack of that will just mean no H.264 acceleration. I can't find a good source document on any of this, just quite a bit of forum searching with a poor noise-signal ratio.

---

