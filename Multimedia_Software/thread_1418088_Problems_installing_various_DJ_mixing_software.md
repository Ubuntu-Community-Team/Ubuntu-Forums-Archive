---
title: "Problems installing various DJ mixing software"
date: 2010-02-28
forum: Multimedia Software
---

### Post by WebBuddha on 2010-02-28
Dear community,

I did some research for good DJ mixing oftware which runs under ubuntu and without wine, and I've found these four.
1. OpenDJmix -> [www.opendjmix.info](www.opendjmix.info) 
2. BPMDJ -> bpmdj.yellowcouch.org/index.html 
3. DJplay -> djplay.sourceforge.net 
4. Ultramixxer -> [www.ultramixxer.com](www.ultramixxer.com)

3 and 4 are not my favourites because nr. 3 seems to be not "finished" and nr 4 has got some memoryleaks after 60-90min and interupptions.

My knowledge with ubuntu and my english is "lala", so please be patient. ;-)

BPMDJ: ./configure runs fine and without any errormsg. If I run make I got those...
> User Interface Resources:
Resource files:
Source Files:
  [cpp] profile-clock.o
 [link] profile-clock
 [test] clock - 10 seconds
Compiling: 1 at a time
  [cpp] index.o
In file included from files.h++:3,
                 from period-type.h++:1,
                 from type-operations.h++:2,
                 from index.h++:3,
                 from index.c++:18:
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = unsigned char]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = Data]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
  [cpp] data-io.o
data-io.c++: In member function ‘virtual int DataTexter::read_fileformat_versionnr()’:
data-io.c++:484: warning: ignoring return value of ‘int fscanf(FILE*, const char*, ...)’, declared with attribute warn_unused_result
data-io.c++: In member function ‘void DataBinner::mmap_textfile()’:
data-io.c++:575: warning: ignoring return value of ‘int fileno(FILE*)’, declared with attribute warn_unused_result
In file included from data-io.c++:6:
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = Data]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = double]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = float]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = long long unsigned int]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = unsigned int]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = short unsigned int]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = unsigned char]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = long long int]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = int]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = short int]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = signed char]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
   [ar] data.a
 [link] index-demo
 [link] idx2txt
  [cpp] song-slot.o
  [cpp] player-config.o
  [cpp] selector.o
selector.c++: In member function ‘virtual void SongSelectorLogic::doAutoMix()’:
selector.c++:1388: warning: format not a string literal and no format arguments
  [cpp] fragment-player.o
  [cpp] dsp-drivers.o
  [cpp] dsp-oss.o
dsp-oss.c++: In member function ‘virtual void dsp_oss::write(stereo_sample2)’:
dsp-oss.c++:93: warning: ignoring return value of ‘ssize_t write(int, const void*, size_t)’, declared with attribute warn_unused_result
  [cpp] dsp-alsa.o
dsp-alsa.c++: In member function ‘virtual void dsp_alsa::write(stereo_sample2)’:
dsp-alsa.c++:64: warning: dereferencing pointer ‘<anonymous>’ does break strict-aliasing rules
dsp-alsa.c++:64: note: initialized from here
  [cpp] dsp-none.o
  [cpp] dsp-jack.o
   [ar] dsp.a
  [cpp] bpmdj.o
In file included from files.h++:3,
                 from period-type.h++:1,
                 from type-operations.h++:2,
                 from index.h++:3,
                 from song-slot.h++:7,
                 from config.h++:8,
                 from song.h++:6,
                 from fragment-player.h:22,
                 from bpmdj.h++:9,
                 from bpmdj.c++:12:
array.h++: In member function ‘Data Array<D, T>::getField(QString) [with int D = 0, T = unsigned char]’:
array.h++:282: warning: ‘<anonymous>’ may be used uninitialized in this function
  [cpp] authors.o
authors.cpp:1: error: expected primary-expression at end of input
authors.cpp:1: error: expected ‘,’ or ‘;’ at end of input
make[1]: *** [authors.o] Fehler 1
make: *** [.compile] Fehler 2


OpenDJmix: ./configure runs also smoothly, but make won't
> make  all-recursive
make[1]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0'
Making all in lib
make[2]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib'
Making all in config
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/config'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/config'
Making all in db
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/db'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/db'
Making all in error
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/error'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/error'
Making all in math
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/math'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/math'
Making all in sys
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/sys'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/sys'
Making all in time
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/time'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/time'
Making all in types
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/types'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/types'
Making all in xml
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/xml'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib/xml'
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib'
make[3]: Für das Ziel »all-am« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib'
make[2]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib'
Making all in kernel
make[2]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel'
Making all in beatmgr
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/beatmgr'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/beatmgr'
Making all in filter
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter'
Making all in pan
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter/pan'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter/pan'
Making all in tonefilter
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter/tonefilter'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter/tonefilter'
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter'
make[4]: Für das Ziel »all-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter'
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/filter'
Making all in ladspa
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/ladspa'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/ladspa'
Making all in midi
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/midi'
Making all in Numark
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/midi/Numark'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/midi/Numark'
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/midi'
make[4]: Für das Ziel »all-am« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/midi'
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/midi'
Making all in mixer
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/mixer'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/mixer'
Making all in output
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/output'
make[3]: Für das Ziel »all« ist nichts zu tun.
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/output'
Making all in source
make[3]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source'
Making all in cda
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/cda'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/cda'
Making all in external
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/external'
Making all in Jack
make[5]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/external/Jack'
make[5]: Für das Ziel »all« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/external/Jack'
make[5]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/external'
make[5]: Für das Ziel »all-am« ist nichts zu tun.
make[5]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/external'
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/external'
Making all in metronome
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/metronome'
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/metronome'
Making all in mp3
make[4]: Betrete Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/mp3'
g++ -DHAVE_CONFIG_H -I. -I../../..    -DQT_NO_DEBUG -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED  -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I/usr/X11R6/include -I.   -D__STDC_LIMIT_MACROS -I/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib  -I.. -DQT_NO_DEBUG -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED  -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4 -I. -I/usr/X11R6/include -I.   -D__STDC_LIMIT_MACROS -I/home/maggus/Desktop/OpenDJMix-Beta-1.0/lib -MT mp3decoder.o -MD -MP -MF .deps/mp3decoder.Tpo -c -o mp3decoder.o mp3decoder.cpp
In file included from mp3decoder.cpp:38:
/usr/lib/gcc/i486-linux-gnu/4.4.1/include/emmintrin.h:32:3: error: #error "SSE2 instruction set not enabled"
make[4]: *** [mp3decoder.o] Fehler 1
make[4]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source/mp3'
make[3]: *** [all-recursive] Fehler 1
make[3]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel/source'
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0/kernel'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/maggus/Desktop/OpenDJMix-Beta-1.0'
make: *** [all] Fehler 2


Thanks in Advance

WebBuddha

---

### Post by elliotn on 2010-02-28
Try mixxx
sudo apt-get install mixxx

This is more like virtualDj and if familiar with it then u can work it out

---

### Post by WebBuddha on 2010-02-28
Mixxx is ok, but I want to try some different applications.

---

