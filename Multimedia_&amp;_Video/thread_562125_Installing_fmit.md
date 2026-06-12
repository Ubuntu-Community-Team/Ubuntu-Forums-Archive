---
title: "Installing fmit"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by milad on 2007-09-28
I installed fmit (it's a music tuner) from Ubuntu repos but when I try to run it i get this error:

```
milad@milad-desktop:~$ fmit
Free Music Instrument Tuner version 0.96.7 built at Dec 12 2006 16:32:55
Install directory '/usr'
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
CaptureThread: INFO: Built in transports
CaptureThread: INFO:    JACK   unavailable
CaptureThread: INFO:    ALSA   available
CaptureThread: INFO: Auto detecting a working transport ... using ALSA
CaptureThread: INFO: ALSA: try to set format to Signed 16 bit Little Endian success
CaptureThread: WARNING: ALSA: cannot set channel count to one (2 instead)
CaptureThread: INFO: ALSA: try to set sampling rate to 96000 failed
CaptureThread: INFO: ALSA: try to set sampling rate to 48000 success
Segmentation fault (core dumped)

```

Does anybody know a solution for this?

I tried to get the latest source and compile it myself, but during the MAKE process I get this error:

```
rm.o MonoQuantizer.o LatencyMonoQuantizer.o DummyMonoQuantizer.o AutoQSettings.o CaptureThread_moc.o CustomInstrumentTunerForm_moc.o MonoQuantizer_moc.o ConfigForm_moc.o InstrumentTunerForm_moc.o ConfigForm.o InstrumentTunerForm.o modules/libmodules.a ../libs/Music/libMusic.a ../libs/CppAddons/libCppAddons.a -lglut -lGLU -lGL  -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi   -lm -lfftw3 -ljack -lasound -lm -ldl -lpthread -lfftw3 -lqt-mt -lSM -lICE -lX11 -lXext -lXmu -lXt -lXi
make[3]: Leaving directory `/home/milad/Desktop/fmit-0.97.6/src'
make[2]: Leaving directory `/home/milad/Desktop/fmit-0.97.6/src'
Making all in tr
make[2]: Entering directory `/home/milad/Desktop/fmit-0.97.6/tr'
/bin/lupdate -verbose ../src/*.cpp ../src/*.h ../ui/*.ui -ts fmit_fr.ts
/bin/bash: /bin/lupdate: No such file or directory
make[2]: *** [fmit_fr.qm] Error 127
make[2]: Leaving directory `/home/milad/Desktop/fmit-0.97.6/tr'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/milad/Desktop/fmit-0.97.6'
make: *** [all] Error 2

```

:(:(:(

---

### Post by plantman on 2008-01-31
I want to install it and run it. I keep getting an error: "Error: JACK: cannot create client, JACK deamon is running?" I am a total newbie and have not used the terminal much. Am I in the ballpark?

---

### Post by Jazzyman on 2008-02-18
lupdate (and lrelease) are located in /usr/bin, but the installer is looking for them in /bin.  Just symlink them and it should work:

sudo ln -s /usr/bin/lupdate /bin/lupdate
sudo ln -s /usr/bin/lrelease /bin/lrelease

Hope this helps

---

