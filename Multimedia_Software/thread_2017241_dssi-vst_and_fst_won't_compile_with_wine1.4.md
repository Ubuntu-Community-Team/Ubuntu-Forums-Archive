---
title: "dssi-vst and fst won't compile with wine1.4"
date: 2012-07-05
forum: Multimedia Software
---

### Post by JollyBard on 2012-07-05
I'm on Ubuntu 12.04, and I used the minimal/netinstall CD. I have various audio packages installed, and I use XFCE with Openbox (partly because openbox-session does not load for some reason and I'm too lazy to fix it, partly because using XFCE adds some app integration)

I kind of need windows VSTs for my band and recordings, but after an upgrade last week (though I think I might have been a bit late), dssi-vst pretty much stopped working. Rosegarden and Qtractor, upon loading VSTs, would freeze and I would have to manually kill them. I haven't found a working alternative, except an external VST host running under wine, but it would be much more functional to have them hosted by the DAW, for automation purposes and such.

So I tried to reinstall dssi-vst, only to find that there was just the 32-bit version remaining. Even if I have some multilib packages installed, it still had to change a lot of stuff to 32bit, which ***** up Qtractor and Rosegarden's dependencies, more precisely liblo7. Knowing that it would be a bad idea to compile Qtractor manually, I tried compiling dssi-vst instead. But then, this happens:

```
~/dssi-vst$ make
wineg++ -m32 -Ivestige -Wall -fPIC dssi-vst-server.cpp -o dssi-vst-server  -L. -lremoteplugin.w32 -lpthread
/usr/bin/ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/x86_64-linux-gnu/wine/libwinecrt0.a(exe_entry.o)) to format elf32-i386 (dssi-vst-server.04FZay.o) is not supported
winebuild: /usr/bin/ld failed with status 1
winegcc: winebuild failed
make: *** [dssi-vst-server.exe.so] Error 2

```

I have no idea what's going on here.

I tried getting the unstable wine1.5, with no success. I tried installing an old package of dssi-vst:amd64 but it needed wine1.3. I tried installing wine1.3 but it needed deprecated packages. Now it's getting frustrating.

So, then I thought, "do I really need dssi-vst? There must be other ways..." so I googled upon fst. Tried compiling it, and it returned exactly the same error.

So, I resigned, and installed dssi-vst:i386, and tried compiling qtractor manually. But it also fails:
./configure:
```
Qtractor 0.5.5

  Build target . . . . . . . . . . . . . . . . . . .: release

  JACK Audio Connection Kit support  . . . . . . . .: yes
  ALSA MIDI Sequencer support  . . . . . . . . . . .: yes
  General audio file support (libsndfile)  . . . . .: yes
  Ogg Vorbis audio file support (libvorbis)  . . . .: yes
  MPEG-1 Audio Layer 3 file support (libmad) . . . .: yes
  Sample-rate conversion support (libsamplerate) . .: yes
  Pitch-shifting support (librubberband) . . . . . .: yes
  OSC service support (liblo)  . . . . . . . . . . .: no
  Archive/Zip file support (zlib)  . . . . . . . . .: yes
  IEEE 32bit float optimizations . . . . . . . . . .: yes
  SSE optimization support (x86) . . . . . . . . . .: yes
  LADSPA Plug-in support . . . . . . . . . . . . . .: yes
  DSSI Plug-in support . . . . . . . . . . . . . . .: yes
  VST Plug-in support  . . . . . . . . . . . . . . .: yes
  LV2 Plug-in support  . . . . . . . . . . . . . . .: yes
  LV2 Plug-in support (libslv2) (DEPRECATED) . . . .: no
  LV2 Plug-in support (liblilv)  . . . . . . . . . .: yes
  LV2 Plug-in UI instantiation (libsuil) . . . . . .: yes
  LV2 Plug-in QT4 UI support . . . . . . . . . . . .: yes
  LV2 Plug-in GTK UI support . . . . . . . . . . . .: yes
  LV2 Plug-in External UI support  . . . . . . . . .: yes
  LV2 Plug-in MIDI/Event support . . . . . . . . . .: yes
  LV2 Plug-in MIDI/Atom support  . . . . . . . . . .: yes
  LV2 Plug-in Worker/Schedule support  . . . . . . .: yes
  LV2 Plug-in State support  . . . . . . . . . . . .: yes
  LV2 Plug-in State Files support (FUBAR)  . . . . .: no
  LV2 Plug-in Programs support . . . . . . . . . . .: yes
  LV2 Plug-in Presets support  . . . . . . . . . . .: yes
  LV2 Plug-in Time support . . . . . . . . . . . . .: yes

  JACK Session support . . . . . . . . . . . . . . .: yes
  JACK Latency support . . . . . . . . . . . . . . .: yes

  X11 Unique/Single instance . . . . . . . . . . . .: no
  VeSTige header support . . . . . . . . . . . . . .: no
  Gradient eye-candy . . . . . . . . . . . . . . . .: yes
  Debugger stack-trace (gdb) . . . . . . . . . . . .: no

  Install prefix . . . . . . . . . . . . . . . . . .: /usr/local
```

sudo make:
```
qtractorLv2Plugin.cpp:975:62: error: ‘lilv_port_get_index’ was not declared in this scope
qtractorLv2Plugin.cpp: In function ‘const void* qtractor_lv2_get_port_value(const char*, void*, uint32_t*, uint32_t*)’:
qtractorLv2Plugin.cpp:1006:58: error: ‘lilv_port_get_index’ was not declared in this scope
qtractorLv2Plugin.cpp: In constructor ‘qtractorLv2Plugin::qtractorLv2Plugin(qtractorPluginList*, qtractorLv2PluginType*)’:
qtractorLv2Plugin.cpp:1728:73: error: ‘lilv_plugin_get_related’ was not declared in this scope
qtractorLv2Plugin.cpp:1732:50: error: ‘lilv_world_load_resource’ was not declared in this scope
qtractorLv2Plugin.cpp:1754:45: error: ‘lilv_plugin_get_port_by_designation’ was not declared in this scope
qtractorLv2Plugin.cpp:1756:60: error: ‘lilv_port_get_index’ was not declared in this scope
qtractorLv2Plugin.cpp: In member function ‘virtual bool qtractorLv2Plugin::loadPreset(const QString&)’:
qtractorLv2Plugin.cpp:3132:2: error: ‘LilvState’ was not declared in this scope
qtractorLv2Plugin.cpp:3132:13: error: ‘state’ was not declared in this scope
qtractorLv2Plugin.cpp:3133:68: error: ‘lilv_state_new_from_world’ was not declared in this scope
qtractorLv2Plugin.cpp:3141:46: error: ‘lilv_state_restore’ was not declared in this scope
qtractorLv2Plugin.cpp:3144:23: error: ‘lilv_state_free’ was not declared in this scope
qtractorLv2Plugin.cpp: In member function ‘virtual bool qtractorLv2Plugin::savePreset(const QString&)’:
qtractorLv2Plugin.cpp:3153:2: error: ‘LilvState’ was not declared in this scope
qtractorLv2Plugin.cpp:3153:13: error: ‘state’ was not declared in this scope
qtractorLv2Plugin.cpp:3157:59: error: ‘lilv_state_new_from_instance’ was not declared in this scope
qtractorLv2Plugin.cpp:3162:58: error: ‘lilv_state_set_label’ was not declared in this scope
qtractorLv2Plugin.cpp:3179:56: error: ‘lilv_state_save’ was not declared in this scope
qtractorLv2Plugin.cpp:3181:23: error: ‘lilv_state_free’ was not declared in this scope
make[2]: *** [.obj/qtractorLv2Plugin.o] Error 1
make[2]: Leaving directory `/home/jolly/Downloads/qtractor-0.5.5/src'
make[1]: *** [sub-src-make_default] Error 2
make[1]: Leaving directory `/home/jolly/Downloads/qtractor-0.5.5'
make: *** [src/qtractor] Error 2

```

Yet, I do have liblilv-dev installed. And I can't even compile lilv manually:
```
~/Downloads/lilv-0/lilv-0.14.2$ ./waf configure
Setting top to                           : /home/jolly/Downloads/lilv-0/lilv-0.14.2 
Setting out to                           : /home/jolly/Downloads/lilv-0/lilv-0.14.2/build 
Checking for 'gcc' (c compiler)          : /usr/bin/gcc 
Checking for 'g++' (c++ compiler)        : /usr/bin/g++ 
Checking for program python              : /usr/bin/python 

Global Configuration 
 * Install prefix                                   : /usr/local 
 * Debuggable build                                 : False 
 * Strict compiler flags                            : False 
 * Build documentation                              : False 

Lilv Configuration 
Checking for program pkg-config                     : /usr/bin/pkg-config 
Checking for 'lv2' >= 1.0.
```

Augh! 

Please help.

(PS: I've heard ardour can be compiled with windows VST support, but I didn't really understand how, and I hate ardour's GUI)

---

### Post by dino99 on 2012-07-05
the good place for such request are:
- wine subforum (game & leisure)
- winehq bugzilla & forum

---

### Post by Elfy on 2012-07-05
The best place for vst is here.

---

### Post by howefield on 2012-07-05
Thread moved to the "*Wine*" forum.

---

### Post by JollyBard on 2012-07-06
Could you move it to the most appropriate subforum, then?

---

