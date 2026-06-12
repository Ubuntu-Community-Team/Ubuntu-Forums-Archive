---
title: "LMMS &amp; VeSTige - plugin not found"
date: 2007-08-14
forum: Multimedia Production
---

### Post by Steve H on 2007-08-14
I hoping someone can help get VST support sorted in LMMS for me.

I have recomplied the source as instructed [here]("http://wiki.mindrules.net/doku.php?id=documentation:installation")

I have checked all the dependencies. 

Yet when i go in to LMMS and try to start the  VeSTige plugin i get an error
```

The vestige-plugin wasn´t found
```

All that has been installed is an .xml file. Is this right?

Does anyone else know why this is happening?

Many Thanks

---

### Post by Steve H on 2007-08-16
**bump**

:)

---

### Post by billstei on 2007-08-17
When you run configure did it report back that you would have VST support?  Mine reports like this:

LMMS will be able to use 
        * ALSA for audio- and MIDI-input/output
        * JACK for audio-input/output
        * OSS for audio- and MIDI-input/output
        * SDL for audio-output
        * libvorbis for encoding/decoding OGG-files
        * SDL_sound for sample-decoding
        * libsndfile for sample-decoding
        * LADSPA-plugins
        * STK instrument plugins
        * SingerBot instrument plugin
        * LMMS VST Support Layer (LVSL) for built-in VST-plugin usage


Bill

---

### Post by Frank Carvalho on 2007-12-27
I have problems too with the Vestige plugin. 

I run on an AMD64 machine, with Ubuntu Studio 7.10. 

All installations of the _x86_64 versions of LMMS seem to omit the libvestige.so file - hence no plugin available. (Starting lmms from command-line makes LMMS crash with libvestige.so not found error).

I then tried to compile it from scratch. I got configure running, and got all the required packages to compile libvestige.so. It seems that Vestige relies heavily on the wine-dev package. But compilation failed with a long mismatch of include files:

make[4]: Entering directory `/home/etcetera/Desktop/lmms-0.3.1/plugins/vst_base'
if g++ -DHAVE_CONFIG_H -I. -I. -I../.. -I../../include -I.  -I/usr/local/include/wine/windows -I/usr/include/wine/windows  -m32  -DQT3 -I/usr/include/qt3 -D_REENTRANT -DQT_THREAD_SUPPORT -DPLUGIN_NAME="vstbase" -O2 -fPIC -ftree-vectorize -ftree-loop-linear -g -O2 -ansi -Wall -Wextra -Wno-unused-parameter -Winline -Wdisabled-optimization -fno-exceptions -I/usr/local/include -MT lvsl_server-lvsl_server.o -MD -MP -MF ".deps/lvsl_server-lvsl_server.Tpo" -c -o lvsl_server-lvsl_server.o `test -f 'lvsl_server.cpp' || echo './'`lvsl_server.cpp; \
        then mv -f ".deps/lvsl_server-lvsl_server.Tpo" ".deps/lvsl_server-lvsl_server.Po"; else rm -f ".deps/lvsl_server-lvsl_server.Tpo"; exit 1; fi
In file included from /usr/include/features.h:345,
                 from /usr/include/pthread.h:23,
                 from lvsl_server.cpp:36:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory
/usr/include/wine/windows/unknwn.h:26: warning: ‘struct IUnknown’ has virtual functions but non-virtual destructor
/usr/include/wine/windows/unknwn.h:113: warning: ‘struct IClassFactory’ has virtual functions but non-virtual destructor
/usr/include/wine/windows/objidl.h:67: warning: ‘struct IMarshal’ has virtual functions but non-virtual destructor
/usr/include/wine/windows/objidl.h:267: warning: ‘struct IMarshal2’ has virtual functions but non-virtual destructor
/usr/include/wine/windows/objidl.h:367: warning: ‘struct IStdMarshalInfo’ has virtual functions but non-virtual destructor
/usr/include/wine/windows/objidl.h:447: warning: ‘struct IExternalConnection’ has virtual functions but non-virtual destructor
...

and about a hundred lines more like this.

In other words vst_base does not compile for me. Could this be the reason it is not included in the 64-bit installers?

I suspect the real problem has to do with Wine being a 32-bit environment. As far as I could figure out, Wine currently has a problem with 64-bit compilation, so compiling on 64-bit based on Wine may be a problem right now. But I am only guessing.

---

