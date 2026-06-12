---
title: "Error compiling monkey audio plugin for k3b"
date: 2011-07-11
forum: Multimedia Software
---

### Post by claracc on 2011-07-11
Hello, I am trying to compile monkey's audio plugin [http://prdownloads.sourceforge.net/k3b/k3bmonkeyaudioplugin-3.1.tar.bz2](http://prdownloads.sourceforge.net/k3b/k3bmonkeyaudioplugin-3.1.tar.bz2) for k3b in order to record .ape sound files in a CD with k3b.

I have followed the tips given in this guide [http://stillstup.blogspot.com/2008/09/monkeys-audio-format-playback-in-ubuntu.html](http://stillstup.blogspot.com/2008/09/monkeys-audio-format-playback-in-ubuntu.html), but after .configure and when i try to do the make I obtain the following errors:

ar: /home/clara/k3b: No such file or directory
make[4]: *** [libmonkeyaudio.la] Error 9
make[3]: *** [all-recursive] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2

I also attached an error_make.txt file with the output of make command.

My system is ubuntu 10.04 gnome but I have some kde apps as k3b release 1.91.0

Any help to solve the problem is very welcomed

---

### Post by claracc on 2011-07-13
I have made some advances, changing the name of the directory where I have k3bmonkeyaudioplugin-3.1, removing spaces in the name.

Now, after .configure, when I run make, I obtain the following:

clara@clara1:~/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1$ make
make  all-recursive
make[1]: se ingresa al directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1»
Making all in po
make[2]: se ingresa al directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/po»
make[2]: No se hace nada para «all».
make[2]: se sale del directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/po»
Making all in src
make[2]: se ingresa al directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src»
Making all in libmonkeyaudio
make[3]: se ingresa al directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src/libmonkeyaudio»
Making all in Assembly
make[4]: se ingresa al directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src/libmonkeyaudio/Assembly»
make[4]: No se hace nada para «all».
make[4]: se sale del directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src/libmonkeyaudio/Assembly»
make[4]: se ingresa al directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src/libmonkeyaudio»
make[4]: No se hace nada para «all-am».
make[4]: se sale del directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src/libmonkeyaudio»
make[3]: se sale del directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src/libmonkeyaudio»
make[3]: se ingresa al directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src»
if /bin/bash ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I..  -I./libmonkeyaudio -I/usr/include/kde -I/usr/share/qt3/include -I.  -DBUILD_CROSS_PLATFORM -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT k3bmonkeydecoder.lo -MD -MP -MF ".deps/k3bmonkeydecoder.Tpo" -c -o k3bmonkeydecoder.lo k3bmonkeydecoder.cpp; \
	then mv -f ".deps/k3bmonkeydecoder.Tpo" ".deps/k3bmonkeydecoder.Plo"; else rm -f ".deps/k3bmonkeydecoder.Tpo"; exit 1; fi
In file included from /usr/include/k3baudiodecoder.h:19,
                 from k3bmonkeydecoder.h:19,
                 from k3bmonkeydecoder.cpp:16:
/usr/include/k3bplugin.h:23:23: error: KPluginInfo: No such file or directory
In file included from /usr/include/k3baudiodecoder.h:20,
                 from k3bmonkeydecoder.h:19,
                 from k3bmonkeydecoder.cpp:16:
/usr/include/k3bmsf.h:23:37: error: QtCore/QSharedDataPointer: No such file or directory
k3bmonkeydecoder.cpp:23:30: error: k3bpluginfactory.h: No such file or directory
In file included from /usr/include/k3baudiodecoder.h:19,
                 from k3bmonkeydecoder.h:19,
                 from k3bmonkeydecoder.cpp:16:
/usr/include/k3bplugin.h:35: error: expected initializer before ':' token
In file included from k3bmonkeydecoder.cpp:212:
k3bmonkeydecoder.moc:164: error: expected '}' at end of input
make[3]: *** [k3bmonkeydecoder.lo] Error 1
make[3]: se sale del directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src»
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1/src»
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio «/home/clara/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1»
make: *** [all] Error 2
clara@clara1:~/k3b_monkey_audio_plugin/k3bmonkeyaudioplugin-3.1$ 

Could anybody tell me what these errors mean and how to fix them?. 

Thanks in advance

---

