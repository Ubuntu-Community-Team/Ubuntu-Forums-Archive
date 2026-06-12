---
title: "No 3d games nvidia blank screen."
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by mariodavidpalacio on 2007-05-06
I don't wanna lose much time telling this over and overt again, because I had to in the irc channels. The thing is, my video card (nvidia nv 18 geforce4 mx with all drivers installed)  seems to be set and ready, and it is, except when I try to play games like tremulous, ppracer or scroched 3d (all 3d games). The rest of the games, the ones that already in the Ubuntu FF 7.04 all work just fine. The problem goes like this: i run the game and i can't see anything in my screen. I know it's working because I can hear the sounds but I don't see the menus. If I hit enter enough, in ppracer, I can see the penguin, but nothing else.

I really wanna use Ubuntu but it's so hard to find an answer for this that I'm thinkin' about gettin' back to windows just for the games. I don't know, maybe I'm being too extremist. But damm, I've been looking for an answer for 5 days, and counting.

---

### Post by CarVac on 2007-05-26
If you type into terminal 'glxgears' what happens?

---

### Post by moderatelymodest on 2008-01-05
I think I might have the same problem.
I have a GeForce4 Ti 4600 with restricted drivers.

glxgears works great but when I try to play 3d games all kinds of strange stuff happens.
unreal tournament 2003 and 2004 demos just seem to lock up when I try to play. 
Savage gives me strange graphical glitches and is very sluggish.

I used to be able to play 3d games without problems before. So it guess it's something that came with gutsy.

I'm looking to upgrade my video card as it is kind of old, but still, it would be nice to have it at least work as well as before until then.

---

### Post by AndersonCouncil on 2008-01-11
I have exactly the same GeForce4 MX graphics card and I quite often just get blank or unrendered textures when using 3D games. glxgears works fine for me... yet I can't play any games which is a huge pain as I have to revert back to windows.

I have yet been unsuccessful in finding any real answers!

Here's what some of the graphics look like (FlightGear):

[IMG]http://i133.photobucket.com/albums/q77/CFP-Art/Graphics3.png[/IMG]

---

### Post by moderatelymodest on 2008-01-18
I've done some more testing and I get other problems I believe are related to this.
in World of Padman I get freeze-ups at, what seems to be, random intervals.
The same thing is true for Warzone2100.
This makes both games unplayable.

Does anyone have any clue how to analyze this problem further? :confused:

---

### Post by moderatelymodest on 2008-02-01
I now tested running ut2004demo while simultaneously running top in a terminal.
both Xorg and ut2004 processes went to 100% CPU, just showing the nvidia-intro and then it crashed.

this is on a fresh install of gutsy with restricted nvidia drivers.

output of UT2004.log that might be relevant:
Log: Initializing OpenGLDrv...
Log: binding libGL.so.1
Log: Game class is 'GameInfo'
Log: Bringing Level Entry.myLevel up for play (0) appSeconds: 10.733624...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Browse: NvidiaLogo.ut2?Name=testo?Class=Engine.Pawn?Character=Jakob?team=255
Log: Collecting garbage
Log: Purging garbage
Log: Garbage: objects: 33489->33488; refs: 347148
Log: Game class is 'CinematicGame'
Log: Bringing Level NvidiaLogo.myLevel up for play (0) appSeconds: 12.375644...
ScriptLog: GameInfo::InitGame : bEnableStatLogging False
Log: Created and initialized a new SDL viewport.
Log: ALAudio: Using ALC_EXT_capture to record audio.
ScriptLog: New Player testo id=32af618f3ba1ef8264f8deefed08553c
Log: TTS: No output filename specified.
Log: Enter SetRes: 640x480 Fullscreen 0
Log: OpenGL
Log: GL_VENDOR     : NVIDIA Corporation
Log: GL_RENDERER   : GeForce4 Ti 4600/AGP/SSE2
Log: GL_VERSION    : 1.5.8 NVIDIA 96.39
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
Log: OpenGL: C32 RGB888 Z24 S0
Log: OpenGL: Level of anisotropy is 1.000000 (max 8.000000).
Log: OpenGL: Have 0 multisamples buffers, 0 samples.
Log: OpenGL: Failed to get a multisample GL context
Log: OpenGL: allocated 32 MByte of AGP memory
Log: Startup time: 13.101075 seconds
Log: Precaching: NvidiaLogo.LevelInfo0
Log: Static mesh batches: 508608 vertex bytes, 110460 index bytes
Log: Allocating 32768 byte dynamic index buffer.
Log: Allocating 65536 byte dynamic vertex buffer.
Log: Finished precaching geometry in 0.038 seconds
Log: Finished precaching textures in 0.161 seconds
Log: Unsupported SDL key id (0x13C)
Log: 
Developer Backtrace:
Log: [ 1]  ./ut2004-bin [0x85a5921]
Log: [ 2]  [0xffffe420]
Log: [ 3]  [0xffffe410]
Log: [ 4]  /lib/tls/i686/cmov/libc.so.6(gsignal+0x55) [0xb7d0f875]
Log: [ 5]  /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7d11201]
Log: [ 6]  /usr/lib/libGLcore.so.1 [0xb53f9585]
Log: Unreal Call Stack: FOpenGLRenderInterface::DrawPrimitive <- USkeletalMeshInstance::Render <- FDynamicActor::Render <- RenderLevel <- FLevelSceneNode::Render <- FPlayerSceneNode::Render <- UGameEngine::Draw <- USDLViewport::Repaint <- USDLClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop
Exit: Exiting.
Log: FileManager: Reading 0 GByte 59 MByte 583 KByte 897 Bytes from HD took 6.805871 seconds (2.041136 reading, 4.764735 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Allocation checking disabled
Uninitialized: Log file closed, Fri Feb  1 06:55:45 2008

---

