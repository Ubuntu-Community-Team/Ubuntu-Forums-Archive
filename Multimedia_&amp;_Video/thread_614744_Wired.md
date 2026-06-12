---
title: "Wired"
date: 2007-11-16
forum: Multimedia &amp; Video
---

### Post by ixlam on 2007-11-16
I'm trying to configure and install "wired" (audio software)..  
after running 
>./autogen.sh
> ./configure  

I get this following error when running
> make

g++ -DHAVE_CONFIG_H -I. -I../../src/include   -I/usr/lib/wx/include/gtk2-unicode-release-2.6 -I/usr/include/wx-2.6 -DGTK_NO_CHECK_CASTS -D__WXGTK__ -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DNO_GCC_PRAGMA  -I../samplerate -I../xml -I../save -I../audio -I../libs/WiredAkai/include -I../plugins -I../fileloader -I/opt/gnome/include -I../sequencer -I../redist -I../engine -I../mixer -I../midi -I../midi/portmidi/pm_common -I../midi/portmidi/porttime -I../asm -I../editmidi -I../undo -I../libs/WiredWidgets/src `xml2-config --cflags ` -I../ -I../portaudio/include  -Os -MT MainWindow.o -MD -MP -MF .deps/MainWindow.Tpo -c -o MainWindow.o MainWindow.cpp
In file included from ../dssi/WiredExternalPlugin.h:9,
                 from ../dssi/WiredExternalPluginMgr.h:13,
                 from MainWindow.cpp:25:
../dssi/dssi.h:35:28: error: alsa/seq_event.h: No such file or directory
../dssi/dssi.h:310: error: ‘snd_seq_event_t’ has not been declared
../dssi/dssi.h:324: error: ‘snd_seq_event_t’ has not been declared
../dssi/dssi.h:362: error: ‘snd_seq_event_t’ has not been declared
../dssi/dssi.h:378: error: ‘snd_seq_event_t’ has not been declared
make[2]: *** [MainWindow.o] Error 1


can anyone help please?

---

### Post by wooster on 2007-11-16
Hi, I think the package you are missing is libasound2-dev. Please try the following and let me know if that helps at all.

```
sudo apt-get install libasound2-dev
```

If that doesn't work I'd search around in synaptic for some alsa development packages you might be missing.

---

### Post by ixlam on 2007-11-16
well that got me much further along in the process but now i get 


engine/libengine.a(AudioEngine.o): In function `AudioEngine::GetDefaultAudioSystem()':
AudioEngine.cpp:(.text+0x257): undefined reference to `Pa_GetDefaultHostApi'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::GetDefaultOutputDevice()':
AudioEngine.cpp:(.text+0x269): undefined reference to `Pa_GetDefaultOutputDevice'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::GetDefaultInputDevice()':
AudioEngine.cpp:(.text+0x28b): undefined reference to `Pa_GetDefaultInputDevice'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::SetInputDevice()':
AudioEngine.cpp:(.text+0x313): undefined reference to `Pa_GetDefaultInputDevice'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::SetOutputDevice()':
AudioEngine.cpp:(.text+0x3b9): undefined reference to `Pa_GetDefaultOutputDevice'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::StopStream()':
AudioEngine.cpp:(.text+0xb54): undefined reference to `Pa_IsStreamActive'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::StartStream()':
AudioEngine.cpp:(.text+0xc28): undefined reference to `Pa_IsStreamActive'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::CloseStream()':
AudioEngine.cpp:(.text+0xd46): undefined reference to `Pa_IsStreamActive'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::GetDevices()':
AudioEngine.cpp:(.text+0xe20): undefined reference to `Pa_GetDeviceCount'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::GetAudioSystems()':
AudioEngine.cpp:(.text+0x1010): undefined reference to `Pa_GetHostApiCount'
AudioEngine.cpp:(.text+0x1076): undefined reference to `Pa_GetHostApiInfo'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::GetCpuLoad()':
AudioEngine.cpp:(.text+0x2b0): undefined reference to `Pa_GetStreamCpuLoad'
engine/libengine.a(AudioEngine.o): In function `AudioEngine::GetTime()':
AudioEngine.cpp:(.text+0x2c2): undefined reference to `Pa_GetStreamTime'
engine/libengine.a(Device.o): In function `Device::GetSupportedSettings()':
Device.cpp:(.text+0x160): undefined reference to `Pa_IsFormatSupported'
collect2: ld returned 1 exit status
make[2]: *** [wired] Error 1
make[2]: Leaving directory `/home/_ /Desktop/wired/wired/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/_/Desktop/wired/wired/src'
make: *** [all-recursive] Error 1

looks like you were right about perhaps needing other packages ... question is .. which ones ?...

---

