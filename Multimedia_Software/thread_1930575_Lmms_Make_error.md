---
title: "Lmms Make error"
date: 2012-02-23
forum: Multimedia Software
---

### Post by checoimg on 2012-02-23
I'm folowing the instalation instructions below:

"
Building LMMS got quite simple since 0.4.0 as everything is managed
by cmake now. Therefore make sure you have CMake (>= 2.6.0 recommended) and
then run


mkdir build
cd build
cmake ../
make [COLOR="Red"]( In stuck here )[/COLOR]
sudo make install

If your system does not have "sudo", become root with your preferred mechanism
and run the "make install" command.

With the above commands an out-of-tree build is performed. You can also run
"cmake ." directly in the root of source tree although this is not recommended.
When performing an out-of-tree build after there's already an in-tree build,
make sure to run "make distclean" before running cmake inside build-directory.

If you want to use custom compiler flags simply set the environment variables
CFLAGS and CXXFLAGS.

After running cmake (the 3rd command above) you can see a summary of things
that are going to be built into LMMS or built as plugins. Install the
according libraries and development files if a certain feature is not enabled.
Then remove CMakeCache.txt and run cmake again.

If you want to supply an install prefix to cmake, add the flag:

-DCMAKE_INSTALL_PREFIX=<prefix>

Where <prefix> can be /usr, /usr/local, /opt, etc. The default is /usr/local.
"

Thank you in advance!

---

### Post by checoimg on 2012-02-23
user@user:~/lmms-0.4.13/build$ make
make: *** No targets specified and [COLOR="Red"]no makefile found[/COLOR].  Stop.

---

### Post by mc4man on 2012-02-24
You should post _everything_ that cmake ../ shows

---

### Post by checoimg on 2012-02-24
I repeated the command and this is what I got now. ( I would like a command that would print all installations in a text file for this cases )

user@user:~/lmms-0.4.13/build$ cmake ../
PROCESSOR: x86_64
Machine: x86_64-linux-gnu
-- Target host is 64 bit
-- Found Qt translations in /usr/share/qt4/translations
-- checking for module 'portaudio-2.0'
--   package 'portaudio-2.0' not found
-- Found OggVorbis: /usr/lib/x86_64-linux-gnu/libogg.so;/usr/lib/x86_64-linux-gnu/libvorbis.so;/usr/lib/x86_64-linux-gnu/libvorbisfile.so;/usr/lib/x86_64-linux-gnu/libvorbisenc.so
-- Found ALSA: /usr/lib/x86_64-linux-gnu/libasound.so
-- checking for module 'jack>=0.77'
--   package 'jack>=0.77' not found
-- checking for module 'fluidsynth>=1.0.7'
--   package 'fluidsynth>=1.0.7' not found
-- checking for module 'samplerate>=0.1.8'
--   package 'samplerate>=0.1.8' not found

Installation Summary
--------------------
* Install Directory           : /usr/local
* Use system's libsamplerate  : 

Supported audio interfaces
--------------------------
* ALSA                        : OK
* JACK                        : not found, please install libjack0.100.0-dev (or similiar) ;if you require JACK support
* OSS                         : OK
* PortAudio                   : not found, please install portaudio19-dev (or similiar, version >= 1.9) ;if you require PortAudio support
* PulseAudio                  : OK
* SDL                         : OK

Supported MIDI interfaces
-------------------------
* ALSA                        : OK
* OSS                         : OK
* WinMM                       : <not supported on this platform>

Supported file formats for project export
-----------------------------------------
* WAVE                        : OK
* OGG/VORBIS                  : OK

Optional plugins
----------------
* SoundFont2 player           : not found, libfluidsynth-dev (or similiar);is highly recommended
* Stk Mallets                 : not found, please install libstk0-dev (or similiar) ;if you require the Mallets instrument
* VST-instrument hoster       : not found, please install (lib)wine-dev (or similiar) - 64 bit systems additionally need gcc-multilib and g++-multilib
* VST-effect hoster           : not found, please install (lib)wine-dev (or similiar) - 64 bit systems additionally need gcc-multilib and g++-multilib
* SpectrumAnalyzer            : OK
* CALF LADSPA plugins         : OK
* CAPS LADSPA plugins         : OK
* CMT LADSPA plugins          : OK
* TAP LADSPA plugins          : OK
* SWH LADSPA plugins          : OK
* ZynAddSubFX                 : OK


-----------------------------------------------------------------
IMPORTANT:
after installing missing packages, remove CMakeCache.txt before
running cmake again!
-----------------------------------------------------------------



CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
X11_Xft_LIB (ADVANCED)
    linked by target "RemoteZynAddSubFx" in directory /home/user/lmms-0.4.13/plugins/zynaddsubfx
X11_Xinerama_LIB (ADVANCED)
    linked by target "RemoteZynAddSubFx" in directory /home/user/lmms-0.4.13/plugins/zynaddsubfx

-- Configuring incomplete, errors occurred!

Thank you!

---

### Post by mc4man on 2012-02-25
you are likely missing some dependencies such as - 

libxft-dev libxinerama-dev 

There may be others, plus any missing optional ones as already seen in the prior post
Maybe consider using this ppa for a good build. ect.

[https://launchpad.net/~dns/+archive/sound](https://launchpad.net/~dns/+archive/sound)

---

### Post by checoimg on 2012-02-26
> **mc4man said:**
> you are likely missing some dependencies such as - 

libxft-dev libxinerama-dev 

There may be others, plus any missing optional ones as already seen in the prior post
Maybe consider using this ppa for a good build. ect.

[https://launchpad.net/~dns/+archive/sound](https://launchpad.net/~dns/+archive/sound)

That was all about it! I installed the dependencies and used Alt+F2 to run it with a command.  Thank you mc4man !

Keep Ubuntuing!

---

