---
title: "XBMC and Blender Game Engine crashing after upgrade to 10.10"
date: 2010-10-12
forum: Multimedia Software
---

### Post by svenni on 2010-10-12
Hi,

I'm having trouble using Blender and XBMC after upgrading to Ubuntu 10.10. Whenever I start the Game Engine mode in Blender (by pressing 'P'), Blender crashes. This happens both in the repository version (2.49.2) and with the newest version (2.54 beta).

For some reason, xbmc actually starts without problems now, but earlier the console output was somewhat similar to that of Blender. The output from Blender seems to indicate that there is something wrong with either libc6 or the NVIDIA drivers. The xbmc output (which now works ok) mentioned something about /lib/nvidia-current/libGL.so, if I remember correctly. 

Do you have any ideas (other than a fresh install) that could help me fix or debug this problem?

The output at crash is as follows:

Blender 2.54:
```
./blenderfound bundled python: /pathtoblender2.54/2.54/python
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Detected GL_ARB_multitexture
Detected GL_ARB_shader_objects
Detected GL_ARB_vertex_shader
Detected GL_ARB_fragment_shader
Detected GL_ARB_vertex_program
Detected GL_ARB_depth_texture
Detected GL_EXT_separate_specular_color
*** glibc detected *** ./blender: malloc(): memory corruption: 0x0000000005f14e70 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f1d112bd4b6]
/lib/libc.so.6(+0x7b55f)[0x7f1d112c155f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7f1d112c238e]
./blender(_Znwm+0x1d)[0x15d890d]
./blender(_ZN12SCA_Joystick11GetInstanceEs+0xaa)[0x11eb14a]
./blender(_ZN19SCA_JoystickManagerC1EP16SCA_LogicManager+0x2c)[0x11d85ec]
./blender(_ZN8KX_SceneC1EP16SCA_IInputDeviceS1_P25NG_NetworkDeviceInterfaceRK10STR_StringP5SceneP11RAS_ICanvas+0x4fb)[0x1172c6b]
./blender(StartKetsjiShell+0x7da)[0x113c3ea]
./blender[0xc67d9a]
./blender(wm_operator_invoke+0x143)[0xc300f3]
./blender[0xc30625]
./blender[0xc3079b]
./blender(wm_event_do_handlers+0x3f9)[0xc31219]
./blender(WM_main+0x14)[0xc2ad14]
./blender(main+0x1e2)[0xc29882]
/lib/libc.so.6(__libc_start_main+0xfe)[0x7f1d11264d8e]
./blender(tan+0x1269)[0xc28d49]
======= Memory map: ========
00400000-031c9000 r-xp 00000000 08:11 786586                             /pathtoblender2.54/blender
033c8000-038b2000 rwxp 02dc8000 08:11 786586                             /pathtoblender2.54/blender
038b2000-04039000 rwxp 00000000 00:00 0 
04a7d000-063d9000 rwxp 00000000 00:00 0                                  [heap]
401e6000-401e8000 r-xs 00000000 08:27 277582                             /tmp/glBtoCA7 (deleted)
41ef0000-41f56000 rwxp 00000000 00:05 4945                               /dev/zero
7f1cfd79d000-7f1cfd81d000 rwxs 162a15000 00:05 10641                     /dev/nvidia1
7f1cfd81d000-7f1cfdec5000 rwxp 00000000 00:00 0 
7f1cfdec5000-7f1cfdec9000 r-xp 00000000 08:11 917713                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/zlib.so
7f1cfdec9000-7f1cfe0c9000 ---p 00004000 08:11 917713                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/zlib.so
7f1cfe0c9000-7f1cfe0cb000 rwxp 00004000 08:11 917713                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/zlib.so
7f1cfe0cb000-7f1cfe0d1000 r-xp 00000000 08:11 917730                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha512.so
7f1cfe0d1000-7f1cfe2d0000 ---p 00006000 08:11 917730                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha512.so
7f1cfe2d0000-7f1cfe2d1000 rwxp 00005000 08:11 917730                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha512.so
7f1cfe2d1000-7f1cfe2d6000 r-xp 00000000 08:11 917728                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha256.so
7f1cfe2d6000-7f1cfe4d5000 ---p 00005000 08:11 917728                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha256.so
7f1cfe4d5000-7f1cfe4d6000 rwxp 00004000 08:11 917728                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha256.so
7f1cfe4d6000-7f1cfe4d9000 r-xp 00000000 08:11 917721                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha1.so
7f1cfe4d9000-7f1cfe6d8000 ---p 00003000 08:11 917721                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha1.so
7f1cfe6d8000-7f1cfe6d9000 rwxp 00002000 08:11 917721                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_sha1.so
7f1cfe6d9000-7f1cfe6dc000 r-xp 00000000 08:11 917715                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_md5.so
7f1cfe6dc000-7f1cfe8db000 ---p 00003000 08:11 917715                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_md5.so
7f1cfe8db000-7f1cfe8dc000 rwxp 00002000 08:11 917715                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_md5.so
7f1cfe8dc000-7f1cfe8ea000 r-xp 00000000 08:11 917729                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_pickle.so
7f1cfe8ea000-7f1cfeaea000 ---p 0000e000 08:11 917729                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_pickle.so
7f1cfeaea000-7f1cfeaec000 rwxp 0000e000 08:11 917729                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/_pickle.so
7f1cfeaec000-7f1cfeaef000 r-xp 00000000 08:11 917725                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/fcntl.so
7f1cfeaef000-7f1cfecee000 ---p 00003000 08:11 917725                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/fcntl.so
7f1cfecee000-7f1cfecf0000 rwxp 00002000 08:11 917725                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/fcntl.so
7f1cfecf0000-7f1cfecf4000 r-xp 00000000 08:11 917694                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/select.so
7f1cfecf4000-7f1cfeef4000 ---p 00004000 08:11 917694                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/select.so
7f1cfeef4000-7f1cfeef6000 rwxp 00004000 08:11 917694                     /pathtoblender2.54/2.54/python/lib/python3.1/lib-dynload/select.so
7f1cfeef6000-7f1cff059000 r-xp 00000000 08:27 131269                     /lib/libcrypto.so.0.9.8
7f1cff059000-7f1cff259000 ---p 00163000 08:27 131269                     /lib/libcrypto.so.0.9.8
7f1cff259000-7f1cff266000 r-xp 00163000 08:27 131269                     /lib/libcrypto.so.0.9.8Aborted
```

Blender 2.49:
```
Compiled with Python version 2.6.6.
Checking for installed Python... got it!
YafaRay 0.1.1
~yafrayInterface_t()	delete scene...delete environment...done
YafaRay 0.1.1
~yafrayInterface_t()	delete scene...delete environment...done
YafaRay 0.1.1
Loading plugins ...
Registered background type 'textureback'
Registered background type 'constant'
Registered integrator type 'directlighting'
Registered integrator type 'pathtracing'
Registered material type 'light_mat'
Registered material type 'mask_mat'
Registered volumeregion type 'NoiseVolume'
Registered texture type 'clouds'
Registered texture type 'marble'
Registered texture type 'wood'
Registered texture type 'voronoi'
Registered texture type 'musgrave'
Registered texture type 'distorted_noise'
Registered texture type 'rgb_cube'
Registered texture type 'image'
Registered integrator type 'photonmapping'
Registered material type 'coated_glossy'
Registered background type 'sunsky'
Registered background type 'gradientback'
Registered integrator type 'DebugIntegrator'
Registered shader node type 'texture_mapper'
Registered shader node type 'value'
Registered shader node type 'mix'
Registered shader node type 'layer'
Registered shader node type 'vcolor'
Registered light type 'spherelight'
Registered volumeregion type 'SkyVolume'
Registered light type 'pointlight'
Registered integrator type 'EmissionIntegrator'
Registered material type 'glossy'
Registered light type 'sunlight'
Registered background type 'darksky'
Registered integrator type 'SkyIntegrator'
Registered integrator type 'bidirectional'
Registered light type 'arealight'
Registered light type 'meshlight'
Registered light type 'bg_portal_light'
Registered light type 'directional'
Registered light type 'spotlight'
Registered integrator type 'none'
Registered volumeregion type 'ExpDensityVolume'
Registered volumetric handler type 'beer'
Registered volumetric handler type 'sss'
Registered material type 'glass'
Registered material type 'mirror'
Registered material type 'null'
Registered material type 'rough_glass'
Registered integrator type 'SingleScatterIntegrator'
Registered material type 'blend_mat'
Registered volumeregion type 'UniformVolume'
Registered material type 'shinydiffusemat'
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Detected GL_ARB_multitexture
Detected GL_ARB_shader_objects
Detected GL_ARB_vertex_shader
Detected GL_ARB_fragment_shader
Detected GL_ARB_vertex_program
Detected GL_ARB_depth_texture
Detected GL_EXT_separate_specular_color
*** glibc detected *** blender-bin: malloc(): memory corruption: 0x00000000029a91d0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7febf3c664b6]
/lib/libc.so.6(+0x7b55f)[0x7febf3c6a55f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7febf3c6b38e]
/usr/lib/libstdc++.so.6(_Znwm+0x1d)[0x7febf336bded]
blender-bin(_ZN12SCA_Joystick11GetInstanceEs+0xba)[0xce563a]
blender-bin(_ZN19SCA_JoystickManagerC1EP16SCA_LogicManager+0x37)[0xccf7a7]
blender-bin(_ZN8KX_SceneC1EP16SCA_IInputDeviceS1_P25NG_NetworkDeviceInterfaceP16SND_IAudioDeviceRK10STR_StringP5Scene+0x52c)[0xc6ab2c]
blender-bin(StartKetsjiShell+0x726)[0xc00016]
blender-bin(start_game+0xd3)[0x664543]
blender-bin[0x666d3f]
blender-bin(screenmain+0x6ff)[0x584cff]
blender-bin(main+0x5f4)[0x576204]
/lib/libc.so.6(__libc_start_main+0xfe)[0x7febf3c0dd8e]
blender-bin[0x575409]
======= Memory map: ========
00400000-01009000 r-xp 00000000 08:27 269434                             /usr/bin/blender-bin
01208000-01228000 r--p 00c08000 08:27 269434                             /usr/bin/blender-bin
01228000-013c2000 rw-p 00c28000 08:27 269434                             /usr/bin/blender-bin
013c2000-01467000 rw-p 00000000 00:00 0 
01fe9000-02a3a000 rw-p 00000000 00:00 0                                  [heap]
40735000-40737000 r-xs 00000000 08:27 277618                             /tmp/glPVvIza (deleted)
41320000-41386000 rw-p 00000000 00:05 4945                               /dev/zero
7febd8000000-7febd8021000 rw-p 00000000 00:00 0 
7febd8021000-7febdc000000 ---p 00000000 00:00 0 
7febde6e5000-7febe26e6000 rw-s 00000000 00:10 86228                      /dev/shm/pulse-shm-3636619877
7febe26e6000-7febe26e7000 ---p 00000000 00:00 0 
7febe26e7000-7febe2ee7000 rw-p 00000000 00:00 0 
7febe2ee7000-7febe2f4c000 rw-s 00000000 00:04 86218                      /dev/zero (deleted)
7febe2f4c000-7febe2f57000 r-xp 00000000 08:27 982485                     /usr/lib/yafaray/libshinydiffuse.so
7febe2f57000-7febe3157000 ---p 0000b000 08:27 982485                     /usr/lib/yafaray/libshinydiffuse.so
7febe3157000-7febe3158000 r--p 0000b000 08:27 982485                     /usr/lib/yafaray/libshinydiffuse.so
7febe3158000-7febe3159000 rw-p 0000c000 08:27 982485                     /usr/lib/yafaray/libshinydiffuse.so
7febe3159000-7febe315d000 r-xp 00000000 08:27 982486                     /usr/lib/yafaray/libUniformVolume.so
7febe315d000-7febe335c000 ---p 00004000 08:27 982486                     /usr/lib/yafaray/libUniformVolume.so
7febe335c000-7febe335d000 r--p 00003000 08:27 982486                     /usr/lib/yafaray/libUniformVolume.so
7febe335d000-7febe335e000 rw-p 00004000 08:27 982486                     /usr/lib/yafaray/libUniformVolume.so
7febe335e000-7febe3363000 r-xp 00000000 08:27 982481                     /usr/lib/yafaray/libblendermat.so
7febe3363000-7febe3562000 ---p 00005000 08:27 982481                     /usr/lib/yafaray/libblendermat.so
7febe3562000-7febe3563000 r--p 00004000 08:27 982481                     /usr/lib/yafaray/libblendermat.so
7febe3563000-7febe3564000 rw-p 00005000 08:27 982481                     /usr/lib/yafaray/libblendermat.so
7febe3564000-7febe356b000 r-xp 00000000 08:27 982483                     /usr/lib/yafaray/libSingleScatterIntegrator.so
7febe356b000-7febe376a000 ---p 00007000 08:27 982483                     /usr/lib/yafaray/libSingleScatterIntegrator.so
7febe376a000-7febe376b000 r--p 00006000 08:27 982483                     /usr/lib/yafaray/libSingleScatterIntegrator.so
7febe376b000-7febe376c000 rw-p 00007000 08:27 982483                     /usr/lib/yafaray/libSingleScatterIntegrator.so
7febe376c000-7febe377b000 r-xp 00000000 08:27 982504                     /usr/lib/yafaray/libglass.so
7febe377b000-7febe397a000 ---p 0000f000 08:27 982504                     /usr/lib/yafaray/libglass.so
7febe397a000-7febe397b000 r--p 0000e000 08:27 982504                     /usr/lib/yafaray/libglass.so
7febe397b000-7febe397c000 rw-p 0000f000 08:27 982504                     /usr/lib/yafaray/libglass.so
7febe397c000-7febe397f000 r-xp 00000000 08:27 982488                     /usr/lib/yafaray/libvolumetrics.so
7febe397f000-7febe3b7e000 ---p 00003000 08:27 982488                     /usr/lib/yafaray/libvolumetrics.so
7febe3b7e000-7febe3b7f000 r--p 00002000 08:27 982488                     /usr/lib/yafaray/libvolumetrics.so
7febe3b7f000-7febe3b80000 rw-p 00003000 08:27 982488                     /usr/lib/yafaray/libvolumetrics.so
7febe3b80000-7febe3b84000 r-xp 00000000 08:27 982494                     /usr/lib/yafaray/libExpDensityVolume.so
7febe3b84000-7febe3d83000 ---p 00004000 08:27 982494                     /usr/lib/yafaray/libExpDensityVolume.so
7febe3d83000-7febe3d84000 r--p 00003000 08:27 982494                     /usr/lib/yafaray/libExpDensityVolume.so
7febe3d84000-7febe3d85000 rw-p 00004000 08:27 982494                     /usr/lib/yafaray/libExpDensityVolume.so
7febe3d85000-7febe3d87000 r-xp 00000000 08:27 982480                     /usr/lib/yafaray/libEmptyVolumeIntegrator.so
7febe3d87000-7febe3f86000 ---p 00002000 08:27 982480                     /usr/lib/yafaray/libEmptyVolumeIntegrator.so
7febe3f86000-7febe3f87000 r--p 00001000 08:27 982480                     /usr/lib/yafaray/libEmptyVolumeIntegrator.so
7febe3f87000-7febe3f88000 rw-p 00002000 08:27 982480                     /usr/lib/yafaray/libEmptyVolumeIntegrator.so
7febe3f88000-7febe3f8d000 r-xp 00000000 08:27 982508                     /usr/lib/yafaray/libspotlight.so
7febe3f8d000-7febe418c000 ---p 00005000 08:27 982508                     /usr/lib/yafaray/libspotlight.so
7febe418c000-7febe418d000 r--p 00004000 08:27 982508                     /usr/lib/yafaray/libspotlight.so
7febe418d000-7febe418e000 rw-p 00005000 08:27 982508                     /usr/lib/yafaray/libspotlight.so
7febe418e000-7febe4192000 r-xp 00000000 08:27 982487                     /usr/lib/yafaray/libdirectional.so
7febe4192000-7febe4391000 ---p 00004000 08:27 982487                     /usr/lib/yafaray/libdirectional.so
7febe4391000-7febe4392000 r--p 00003000 08:27 982487                     /usr/lib/yafaray/libdirectional.so
7febe4392000-7febe4393000 rw-p 00004000 08:27 982487                     /usr/lib/yafaray/libdirectional.so
7febe4393000-7febe439e000 r-xp 00000000 08:27 982497                     /usr/lib/yafaray/libarealight.so
7febe439e000-7febe459e000 ---p 0000b000 08:27 982497                     /usr/lib/yafaray/libarealight.so
7febe459e000-7febe459f000 r--p 0000b000 08:27 982497                     /usr/lib/yafaray/libarealight.so
7febe459f000-7febe45a0000 rw-p 0000c000 08:27 982497                     /usr/lib/yafaray/libarealight.soAborted
```

Both version work fine on my laptop with Ubuntu 10.04.

---

### Post by svenni on 2010-10-12
There we go, after a quick reboot the xbmc error is back again. Here is the output from running xbmc in console:

```
xbmc
params.c:OpenConfFile() - Unable to open configuration file "/home/<my username>/.smb/smb.conf":
    No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/<my username>/.smb/smb.conf.append":
    No such file or directory
*** glibc detected *** /usr/share/xbmc/xbmc.bin: malloc(): memory corruption: 0x0000000002af6920 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f3bf7b984b6]
/lib/libc.so.6(+0x7b55f)[0x7f3bf7b9c55f]
/lib/libc.so.6(__libc_malloc+0x6e)[0x7f3bf7b9d38e]
/usr/lib/nvidia-current/libGL.so.1(+0x9ab15)[0x7f3bfbe4fb15]
======= Memory map: ========
00400000-00e96000 r-xp 00000000 08:27 293207                             /usr/lib/xbmc/xbmc.bin
01096000-01099000 r--p 00a96000 08:27 293207                             /usr/lib/xbmc/xbmc.bin
01099000-010d1000 rw-p 00a99000 08:27 293207                             /usr/lib/xbmc/xbmc.bin
010d1000-0113f000 rw-p 00000000 00:00 0 
02ac8000-02c39000 rw-p 00000000 00:00 0                                  [heap]
7f3be4000000-7f3be4021000 rw-p 00000000 00:00 0 
7f3be4021000-7f3be8000000 ---p 00000000 00:00 0 
7f3beab7c000-7f3beab7d000 ---p 00000000 00:00 0 
7f3beab7d000-7f3beb37d000 rw-p 00000000 00:00 0 
7f3bef37e000-7f3bef383000 r-xp 00000000 08:27 266218                     /usr/lib/libXfixes.so.3.1.0
7f3bef383000-7f3bef582000 ---p 00005000 08:27 266218                     /usr/lib/libXfixes.so.3.1.0
7f3bef582000-7f3bef583000 r--p 00004000 08:27 266218                     /usr/lib/libXfixes.so.3.1.0
7f3bef583000-7f3bef584000 rw-p 00005000 08:27 266218                     /usr/lib/libXfixes.so.3.1.0
7f3bef584000-7f3bef58d000 r-xp 00000000 08:27 266223                     /usr/lib/libXcursor.so.1.0.2
7f3bef58d000-7f3bef78c000 ---p 00009000 08:27 266223                     /usr/lib/libXcursor.so.1.0.2
7f3bef78c000-7f3bef78d000 r--p 00008000 08:27 266223                     /usr/lib/libXcursor.so.1.0.2
7f3bef78d000-7f3bef78e000 rw-p 00009000 08:27 266223                     /usr/lib/libXcursor.so.1.0.2
7f3bef78e000-7f3bef790000 r-xp 00000000 08:27 307330                     /usr/lib/gconv/IBM850.so
7f3bef790000-7f3bef98f000 ---p 00002000 08:27 307330                     /usr/lib/gconv/IBM850.so
7f3bef98f000-7f3bef990000 r--p 00001000 08:27 307330                     /usr/lib/gconv/IBM850.so
7f3bef990000-7f3bef991000 rw-p 00002000 08:27 307330                     /usr/lib/gconv/IBM850.so
7f3bef991000-7f3bef994000 r-xp 00000000 08:27 307440                     /usr/lib/gconv/UTF-16.so
7f3bef994000-7f3befb93000 ---p 00003000 08:27 307440                     /usr/lib/gconv/UTF-16.so
7f3befb93000-7f3befb94000 r--p 00002000 08:27 307440                     /usr/lib/gconv/UTF-16.so
7f3befb94000-7f3befb95000 rw-p 00003000 08:27 307440                     /usr/lib/gconv/UTF-16.so
7f3befb95000-7f3beff58000 r--p 00000000 08:27 263208                     /usr/lib/locale/locale-archive
7f3beff58000-7f3bf020b000 r-xp 00000000 08:27 291606                     /usr/lib/libvorbisenc.so.2.0.7
7f3bf020b000-7f3bf040a000 ---p 002b3000 08:27 291606                     /usr/lib/libvorbisenc.so.2.0.7
7f3bf040a000-7f3bf0426000 r--p 002b2000 08:27 291606                     /usr/lib/libvorbisenc.so.2.0.7
7f3bf0426000-7f3bf0427000 rw-p 002ce000 08:27 291606                     /usr/lib/libvorbisenc.so.2.0.7
7f3bf0427000-7f3bf046f000 r-xp 00000000 08:27 291545                     /usr/lib/libFLAC.so.8.2.0
7f3bf046f000-7f3bf066f000 ---p 00048000 08:27 291545                     /usr/lib/libFLAC.so.8.2.0
7f3bf066f000-7f3bf0670000 r--p 00048000 08:27 291545                     /usr/lib/libFLAC.so.8.2.0
7f3bf0670000-7f3bf0671000 rw-p 00049000 08:27 291545                     /usr/lib/libFLAC.so.8.2.0
7f3bf0671000-7f3bf0674000 r-xp 00000000 08:27 131161                     /lib/libgpg-error.so.0.4.0
7f3bf0674000-7f3bf0873000 ---p 00003000 08:27 131161                     /lib/libgpg-error.so.0.4.0
7f3bf0873000-7f3bf0874000 r--p 00002000 08:27 131161                     /lib/libgpg-error.so.0.4.0
7f3bf0874000-7f3bf0875000 rw-p 00003000 08:27 131161                     /lib/libgpg-error.so.0.4.0
7f3bf0875000-7f3bf0885000 r-xp 00000000 08:27 266257                     /usr/lib/libtasn1.so.3.1.9
7f3bf0885000-7f3bf0a84000 ---p 00010000 08:27 266257                     /usr/lib/libtasn1.so.3.1.9
7f3bf0a84000-7f3bf0a85000 r--p 0000f000 08:27 266257                     /usr/lib/libtasn1.so.3.1.9
7f3bf0a85000-7f3bf0a86000 rw-p 00010000 08:27 266257                     /usr/lib/libtasn1.so.3.1.9
7f3bf0a86000-7f3bf0a9f000 r-xp 00000000 08:27 271394                     /usr/lib/libsasl2.so.2.0.23
7f3bf0a9f000-7f3bf0c9e000 ---p 00019000 08:27 271394                     /usr/lib/libsasl2.so.2.0.23
7f3bf0c9e000-7f3bf0c9f000 r--p 00018000 08:27 271394                     /usr/lib/libsasl2.so.2.0.23
7f3bf0c9f000-7f3bf0ca0000 rw-p 00019000 08:27 271394                     /usr/lib/libsasl2.so.2.0.23
7f3bf0ca0000-7f3bf0ca2000 r-xp 00000000 08:27 131156                     /lib/libkeyutils.so.1.3
7f3bf0ca2000-7f3bf0ea1000 ---p 00002000 08:27 131156                     /lib/libkeyutils.so.1.3
7f3bf0ea1000-7f3bf0ea2000 r--p 00001000 08:27 131156                     /lib/libkeyutils.so.1.3
7f3bf0ea2000-7f3bf0ea3000 rw-p 00002000 08:27 131156                     /lib/libkeyutils.so.1.3
7f3bf0ea3000-7f3bf0eaa000 r-xp 00000000 08:27 267289                     /usr/lib/libkrb5support.so.0.1
7f3bf0eaa000-7f3bf10a9000 ---p 00007000 08:27 267289                     /usr/lib/libkrb5support.so.0.1
7f3bf10a9000-7f3bf10aa000 r--p 00006000 08:27 267289                     /usr/lib/libkrb5support.so.0.1
7f3bf10aa000-7f3bf10ab000 rw-p 00007000 08:27 267289                     /usr/lib/libkrb5support.so.0.1
7f3bf10ab000-7f3bf10af000 r-xp 00000000 08:27 131244                     /lib/libattr.so.1.1.0
7f3bf10af000-7f3bf12ae000 ---p 00004000 08:27 131244                     /lib/libattr.so.1.1.0
7f3bf12ae000-7f3bf12af000 r--p 00003000 08:27 131244                     /lib/libattr.so.1.1.0
7f3bf12af000-7f3bf12b0000 rw-p 00004000 08:27 131244                     /lib/libattr.so.1.1.0
7f3bf12b0000-7f3bf130e000 r-xp 00000000 08:27 268147                     /usr/lib/libsndfile.so.1.0.21
7f3bf130e000-7f3bf150e000 ---p 0005e000 08:27 268147                     /usr/lib/libsndfile.so.1.0.21
7f3bf150e000-7f3bf1510000 r--p 0005e000 08:27 268147                     /usr/lib/libsndfile.so.1.0.21
7f3bf1510000-7f3bf1511000 rw-p 00060000 08:27 268147                     /usr/lib/libsndfile.so.1.0.21
7f3bf1511000-7f3bf1515000 rw-p 00000000 00:00 0 
/usr/bin/xbmc: line 88:  2665 Aborted                 (core dumped) /usr/share/xbmc/xbmc.bin "$@"
Crash report available at /home/<my username>/xbmc_crashlog-20101012_124837.log
```

---

### Post by Silver Knight on 2010-10-30
Obligatory "me too" response.  Having this exact same problem with both programs mentioned by the original poster.

---

### Post by svenni on 2010-10-30
I just did a complete reinstall of Ubuntu and the problem went away (I'm glad I always store /home on another partition for easier upgrading).

However, I'm unable to investigate this problem further myself because I wiped out the old install, but if you want to, Silver Knight, I suggest you check out the configuration files for maybe XOrg or anything else related to the graphics driver. Maybe even running the nvidia-settings manager will let you reset everything to defaults or you could delete /etc/xorg.conf to let nvidia-settings create a new config file for you. Just make sure you back up the old one somewhere.

If you want to compare any config files with my new setup, I'll be glad to help you out. I guess it would do good if we could figure out where the error is and maybe file a bug report about it.

---

