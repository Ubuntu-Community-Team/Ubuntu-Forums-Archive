---
title: "I can't build LMMS"
date: 2009-01-21
forum: Multimedia Software
---

### Post by Marcus Derekus on 2009-01-21
OK, I have Ubuntustudio 8.04 and I want to build LMMS from source. I have the one fromn the repos but it is old and doesn't allow time signatuure change. 

So the only way to get the new one is build it from source. Where the problem comes in is that when I try to build using cmake (that is what is required to build LMMS) in gives me this error.

```
colburn@colburn-laptop:~/Desktop/Downloads/lmms-0.4.2/build$ cmake ..
[COLOR="Red"]PROCESSOR: unknown
Machine: i486-linux-gnu
-- Target host is 32 bit
CMake Error: Qt qmake not found!
-- Configuring done[/COLOR]

```

I have qmake installed, so I do not beleive that this is the problem. ANY suggestions WILL do. I installed qmake with the "qt-dev-tools" package as I am pretty sure that is the only way on hardy.

I am probably in the wrong category now that I think of it as this really doesn't have anything to do with multimedia (except LMMS).

---

### Post by mc4man on 2009-01-21
A couple of things.

first maybe run this to ck.
```
sudo apt-get build-dep lmms
```

Then make sure you have cmake installed.

Other possible issues
install libfluidsynth-dev  libfftw3-dev

lmms 0.4 uses libsamplerate0_0.1.3 ( not in hardy

If you want go here
[http://packages.ubuntu.com/intrepid/libsamplerate0](http://packages.ubuntu.com/intrepid/libsamplerate0)
and here
[http://packages.ubuntu.com/intrepid/libsamplerate0-dev](http://packages.ubuntu.com/intrepid/libsamplerate0-dev)

download both to desktop, create a folder in home, put both .deb's inside, cd to it and run dpkg on (don't remove existing
Ex. created folder 'try' in home

> doug@doug-desktop:~/try$ sudo dpkg -i *.deb
[sudo] password for doug: 
(Reading database ... 212710 files and directories currently installed.)
Preparing to replace libsamplerate0 0.1.2-5ubuntu1 (using libsamplerate0_0.1.3-1_i386.deb) ...
Unpacking replacement libsamplerate0 ...
Preparing to replace libsamplerate0-dev 0.1.2-5ubuntu1 (using libsamplerate0-dev_0.1.3-1_i386.deb) ...
Unpacking replacement libsamplerate0-dev ...
Setting up libsamplerate0 (0.1.3-1) ...

Setting up libsamplerate0-dev (0.1.3-1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
doug@doug-desktop:~/try$ 



Here's the cmake after the above for comparison

> doug@doug-desktop:~/stable-0.4/stable-0.4/build$ cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
PROCESSOR: unknown
Machine: i486-linux-gnu
-- Target host is 32 bit
-- Looking for include files LMMS_HAVE_STDINT_H
-- Looking for include files LMMS_HAVE_STDINT_H - found
-- Looking for include files LMMS_HAVE_STDLIB_H
-- Looking for include files LMMS_HAVE_STDLIB_H - found
-- Looking for include files LMMS_HAVE_PTHREAD_H
-- Looking for include files LMMS_HAVE_PTHREAD_H - found
-- Looking for include files LMMS_HAVE_SEMAPHORE_H
-- Looking for include files LMMS_HAVE_SEMAPHORE_H - found
-- Looking for include files LMMS_HAVE_UNISTD_H
-- Looking for include files LMMS_HAVE_UNISTD_H - found
-- Looking for include files LMMS_HAVE_SYS_TYPES_H
-- Looking for include files LMMS_HAVE_SYS_TYPES_H - found
-- Looking for include files LMMS_HAVE_SYS_IPC_H
-- Looking for include files LMMS_HAVE_SYS_IPC_H - found
-- Looking for include files LMMS_HAVE_SYS_SHM_H
-- Looking for include files LMMS_HAVE_SYS_SHM_H - found
-- Looking for include files LMMS_HAVE_SYS_TIME_H
-- Looking for include files LMMS_HAVE_SYS_TIME_H - found
-- Looking for include files LMMS_HAVE_SYS_WAIT_H
-- Looking for include files LMMS_HAVE_SYS_WAIT_H - found
-- Looking for include files LMMS_HAVE_SYS_SELECT_H
-- Looking for include files LMMS_HAVE_SYS_SELECT_H - found
-- Looking for include files LMMS_HAVE_STDARG_H
-- Looking for include files LMMS_HAVE_STDARG_H - found
-- Looking for include files LMMS_HAVE_SIGNAL_H
-- Looking for include files LMMS_HAVE_SIGNAL_H - found
-- Looking for include files LMMS_HAVE_SCHED_H
-- Looking for include files LMMS_HAVE_SCHED_H - found
-- Looking for include files LMMS_HAVE_SYS_SOUNDCARD_H
-- Looking for include files LMMS_HAVE_SYS_SOUNDCARD_H - found
-- Looking for include files LMMS_HAVE_SOUNDCARD_H
-- Looking for include files LMMS_HAVE_SOUNDCARD_H - not found.
-- Looking for include files LMMS_HAVE_FCNTL_H
-- Looking for include files LMMS_HAVE_FCNTL_H - found
-- Looking for include files LMMS_HAVE_SYS_IOCTL_H
-- Looking for include files LMMS_HAVE_SYS_IOCTL_H - found
-- Looking for include files LMMS_HAVE_CTYPE_H
-- Looking for include files LMMS_HAVE_CTYPE_H - found
-- Looking for include files LMMS_HAVE_STRING_H
-- Looking for include files LMMS_HAVE_STRING_H - found
-- Looking for include files LMMS_HAVE_PROCESS_H
-- Looking for include files LMMS_HAVE_PROCESS_H - not found.
-- Looking for include files LMMS_HAVE_LOCALE_H
-- Looking for include files LMMS_HAVE_LOCALE_H - found
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Found Qt-Version 4.3.4
-- Found Qt translations in /usr/share/qt4/translations
-- checking for module 'sndfile>=1.0.11'
--   found sndfile, version 1.0.17
-- Looking for pthread.h
-- Looking for pthread.h - found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found STK: /usr/lib/libstk.so
-- checking for module 'libpulse'
--   found libpulse, version 0.9.10
-- Found PulseAudio Simple: /usr/lib/libpulse.so
-- Looking for vorbis_bitrate_addblock in vorbis
-- Looking for vorbis_bitrate_addblock in vorbis - found
-- Found OggVorbis: /usr/lib/libogg.so;/usr/lib/libvorbis.so;/usr/lib/libvorbisfile.so;/usr/lib/libvorbisenc.so
-- Looking for snd_seq_create_simple_port in asound
-- Looking for snd_seq_create_simple_port in asound - found
-- Found ALSA: /usr/lib/libasound.so
-- Looking for include files LMMS_HAVE_MACHINE_SOUNDCARD_H
-- Looking for include files LMMS_HAVE_MACHINE_SOUNDCARD_H - not found.
-- Looking for include files LMMS_HAVE_LINUX_AWE_VOICE_H
-- Looking for include files LMMS_HAVE_LINUX_AWE_VOICE_H - not found.
-- Looking for include files LMMS_HAVE_AWE_VOICE_H
-- Looking for include files LMMS_HAVE_AWE_VOICE_H - not found.
-- Looking for include files LMMS_HAVE__USR_SRC_SYS_I386_ISA_SOUND_AWE_VOICE_H
-- Looking for include files LMMS_HAVE__USR_SRC_SYS_I386_ISA_SOUND_AWE_VOICE_H - not found.
-- Looking for include files LMMS_HAVE__USR_SRC_SYS_GNU_I386_ISA_SOUND_AWE_VOICE_H
-- Looking for include files LMMS_HAVE__USR_SRC_SYS_GNU_I386_ISA_SOUND_AWE_VOICE_H - not found.
-- Looking for C++ include sys/asoundlib.h
-- Looking for C++ include sys/asoundlib.h - found
-- Looking for C++ include alsa/asoundlib.h
-- Looking for C++ include alsa/asoundlib.h - found
-- Looking for snd_pcm_resume in asound
-- Looking for snd_pcm_resume in asound - found
-- checking for module 'jack>=0.77'
--   found jack, version 0.109.2
-- checking for module 'fftw3f>=3.0.0'
--   found fftw3f, version 3.1.2
-- checking for module 'fluidsynth>=1.0.7'
--   found fluidsynth, version 1.0.7
-- Looking for wine_init in wine
-- Looking for wine_init in wine - found
-- Looking for C++ include windows.h
-- Looking for C++ include windows.h - found
-- checking for module 'samplerate>=0.1.3'
--   found samplerate, version 0.1.3

Installation Summary
--------------------
* Install Directory           : /usr
* Use system's libsamplerate  : TRUE

Supported audio interfaces
--------------------------
* ALSA                        : OK
* JACK                        : OK
* OSS                         : OK
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
* SoundFont2 player           : OK
* Stk Mallets                 : OK
* VST-instrument hoster       : OK
* VST-effect hoster           : OK
* SpectrumAnalyzer            : OK
* CAPS LADSPA plugins         : OK
* CMT LADSPA plugins          : OK
* TAP LADSPA plugins          : OK
* SWH LADSPA plugins          : OK


-----------------------------------------------------------------
IMPORTANT:
after installing missing packages, remove CMakeCache.txt before
running cmake again!
-----------------------------------------------------------------



-- Configuring done
-- Generating done
-- Build files have been written to: /home/doug/stable-0.4/stable-0.4/build
doug@doug-desktop:~/stable-0.4/stable-0.4/build$

---

### Post by Marcus Derekus on 2009-01-21
Thanks for the reply! But I don't think it is a problem with LMMS at all, I know I have all of the require ments for lmms as I have 3.1 (actuall I JUST removed it) installed. Unfortunately LMMS 4.2 isn't in the hardy repos.

I think the problem is with Cmake not knowing where qmake is. Do I need to make a symbolic link or something? I don't know why it isn't working.

See your using Ubuntu 8.10  aren't you? I believe qmake is it's own separate package in intrepid where as it is part of qt-dev-tools in hardy.

I need to get cmake to recognize qmake I believe. Thanks a lot for the help though.

---

### Post by mc4man on 2009-01-21
Edit : sorry - the lmms is only for intrepid

[https://launchpad.net/~tobydox/+archive](https://launchpad.net/~tobydox/+archive)

---

### Post by mc4man on 2009-01-22
> See your using Ubuntu 8.10 aren't you?
Well I have a new Intrepid I'm setting up but no, what I posted was from Hardy.

Went ahead and did a make and make install, works fine. (on Hardy
I do a lot of building of media apps, mplayer, vlc, transcode, ffmpeg, ect., but simply running the build-deps (added a few packages), ck.ing on the other 2 and upgrading libsamplerate0  to intrepid versions and it configured, built fine.

Have you tried all that? (there's no literal "qmake", do you have libqt4-dev installed?

Edit: did a quick test. Made a checkinstall package from above hardy build and installed it on another hardy that had lmms 3.2

Removed lmms and lmms-common.
Made sure libfluidsynth and libfftw3 were installed (no need for -dev's
Upgraded libsamplerate0 to the intrepid version (0.1.3

Installed and wouldn't run

Installed libqt4-core, libqt4-gui

Now it runs fine, so I'd say your problem is not having the libqt4 packages (including -dev's
(also assuming you have the normal build packages installed


If you really can't get done and want I'll upload the .deb to mediafire (lmms-0.4.2 for hardy

---

### Post by Marcus Derekus on 2009-01-22
Ok, great. I'm gonna try all of this stuff out if I can, no sweat, I configure stuff on Ubuntu all the time. But a .deb link would be great just in case cuz I need LMMS and if I don't have time to configure or my computer just won't then having the .deb would be a life saver.

Plus, I don't even know how often i'll use cmake, it is LMMS that I am mainly wanting. Thanks a lot! I'll be back tomorrow later in the day, so i'll give you my results and such then. Thanks a lot!

---

### Post by mc4man on 2009-01-22
Here you go
First....

If not previously installed, install lmms from hardy repo, then remove (satisfies most run dep's
Make sure lmms-common **is not installed**

Check in synaptic for 

 libfluidsynth1 ; libfftw3-3 ; libqt4-core ; libqt4-gui, install if not already

Go here and do a direct download and install to upgrade libsamplerate0 (don't remove current ver. let Gdebi install

[http://packages.ubuntu.com/intrepid/libsamplerate0](http://packages.ubuntu.com/intrepid/libsamplerate0)

Then you can install .deb

[http://www.mediafire.com/file/mtzozzzlmyn/lmms_0.4.2-1ubuntu2-1_i386.deb](http://www.mediafire.com/file/mtzozzzlmyn/lmms_0.4.2-1ubuntu2-1_i386.deb)


To install a proper menu item in sound & video after installing,

If you have the source (or go get it here, you can delete after done, Assumes source is in home folder -> stable-0.4/stable-0.4/

```
svn co https://lmms.svn.sf.net/svnroot/lmms/branches/lmms stable-0.4
```

Then run this command 
```
cp ~/stable-0.4/stable-0.4/data/lmms.desktop ~/.local/share/applications/
```


Or do this
Create an new text file in home folder

Name it ```
lmms.desktop
```

Run in terminal
```
gedit ~/lmms.desktop
```
Copy and paste this in 

> [Desktop Entry]
Name=Linux MultiMedia Studio
GenericName=music production suite
GenericName[ca]=Programari de producció musical
GenericName[de]=Software zur Musik-Produktion
Comment=easy music production for everyone!
Comment[ca]=Producció fàcil de música per a tothom!
Icon=/usr/share/lmms/themes/default/icon.png
Exec=/usr/bin/lmms
Terminal=false
Type=Application
Encoding=UTF-8
Categories=Application;AudioVideo;Qt
MimeType=application/x-lmms-project

save, and then run this

```
cp ~/lmms.desktop  ~/.local/share/applications/
```

---

### Post by simtaalo on 2009-01-22
> **mc4man said:**
> Edit : sorry - the lmms is only for intrepid

[https://launchpad.net/~tobydox/+archive](https://launchpad.net/~tobydox/+archive)

if you look on that page you will see you can select hardy from the drop down menu.

IMO the best way to install lmms is to add that repo to your sources.list. this will give you the latest version of lmms.

also come join us in the lmms irc channel on freenode ##lmms

---

### Post by mc4man on 2009-01-22
> if you look on that page you will see you can select hardy from the drop down menu.
That's what I first saw, then noticed lmms is only listed as an Intrepid build, so didn't try.
Though maybe if you ugrade libsamplerate0 to intrepid it would install/run right...?

---

### Post by simtaalo on 2009-01-22
> **mc4man said:**
> That's what I first saw, then noticed lmms is only listed as an Intrepid build, so didn't try.
Though maybe if you ugrade libsamplerate0 to intrepid it would install/run right...?

yuo don't need to worry bout any of that, simply add the lines to your sources.list and then install and should all be fine.

---

### Post by Marcus Derekus on 2009-01-22
@simtaalo

when I installed the lmms in the link you gave the package said I din't have libasound 2, which I do.

@MC4MAN

Thanks! I tried installing the libsamplerate0 and libqt-dev and the source built fine!

Now the problem is that LMMS won't use my alsa driver, it is using the dummy driver so my output is "buzzy". IF you can help great!

EDIT: well, it is using dummy, but now it sounds fine, I'm marking this as solved!lol 

Btw how do I thank you guys (meaning oficially on the forum). I remember that there used to be a little button at the end of each post by that person that was titled "thank". It looks like thanking has been removed???

---

### Post by simtaalo on 2009-01-22
wierd it asked for the extra package, i never got that.

seems you got it all working now, do come join us in the irc room, ##lmms on freenode.

share work, chat, talk about different ways lmms could progress :) all welcome

---

### Post by Marcus Derekus on 2009-01-22
Great! I surely will.

---

