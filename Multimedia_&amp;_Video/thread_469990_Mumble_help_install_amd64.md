---
title: "Mumble help install amd64"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by skatedawe on 2007-06-10
Im having problem to install mumble with amd64 architecture.

What is mumble?: "Mumble is a low-latency, high quality voice chat software primarily intended for use while gaming."

Their homepage: [http://mumble.sourceforge.net/](http://mumble.sourceforge.net/)

There is only source packages, 32bit version and windows version. So im going for the source package.

Im downloding it @ [http://sourceforge.net/project/showfiles.php?group_id=147372](http://sourceforge.net/project/showfiles.php?group_id=147372) - 
[http://downloads.sourceforge.net/mumble/mumble-0.9.4.tar.bz2?modtime=1162211286&big_mirror=0](http://downloads.sourceforge.net/mumble/mumble-0.9.4.tar.bz2?modtime=1162211286&big_mirror=0)

After downloading it, packing up.

Then following the INSTALL (for depencies):

```
Pre-requisites
==============
Mumble and murmur depends on Qt version 4.1.0 or above; either the opensource
or commercial versions will do.
Please see http://www.trolltech.com/qt/ for more information. As we use the Qt
build system, it's important that you have a fully functional Qt installation.

The mumble build uses pre-comiled headers. If you use GCC, make sure it's at
least version 3.4.

Mumble depends on libspeex. See http://www.speex.org for details. Note that
you need the latest "unstable" version to compile. (Speex generally has high
code quality, the the svn version is probably even more stable than the
released unstable version).

Mumble needs the Boost C++ library. http://www.boost.org

You may need to adjust the paths in mumble.pro, murmur.pro and mumble.pri to
reflect where your installed versions of dependant libraries are.

Linux pre-requisites
====================

Mumble needs libasound2 (the ALSA developer libraries) as well as the developer
libraries for Xevie.

The Linux version of the client has been tested on Ubuntu 6.06. It may work on
other updated distributions. The server should work on any modern UNIX-based
distribution and on Windows.

Building Mumble
===============

To build mumble, type
qmake mumble.pro
lrelease mumble.pro
make

You may need to edit mumble.pro to reflect the installation paths you use for
libraries.

Building Murmur
===============

To build murmur, type
qmake murmur.pro
make
```

I get following errors long down in the compilation...:

```
In file included from ALSAAudio.cpp:31:
ALSAAudio.h:36:28: error: alsa/asoundlib.h: No such file or directory
ALSAAudio.h:57: error: ISO C++ forbids declaration of &#8216;snd_pcm_t&#8217; with no type
ALSAAudio.h:57: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
ALSAAudio.cpp: In member function &#8216;virtual void ALSAAudioInput::run()&#8217;:
ALSAAudio.cpp:69: error: &#8216;snd_pcm_t&#8217; was not declared in this scope
ALSAAudio.cpp:69: error: &#8216;capture_handle&#8217; was not declared in this scope
ALSAAudio.cpp:71: error: &#8216;snd_pcm_hw_params_t&#8217; was not declared in this scope
ALSAAudio.cpp:71: error: &#8216;hw_params&#8217; was not declared in this scope
ALSAAudio.cpp:78: error: &#8216;SND_PCM_STREAM_CAPTURE&#8217; was not declared in this scope
ALSAAudio.cpp:78: error: &#8216;snd_pcm_open&#8217; was not declared in this scope
ALSAAudio.cpp:81: error: &#8216;snd_pcm_hw_params_malloc&#8217; was not declared in this scope
ALSAAudio.cpp:82: error: &#8216;snd_pcm_hw_params_any&#8217; was not declared in this scope
ALSAAudio.cpp:83: error: &#8216;SND_PCM_ACCESS_RW_INTERLEAVED&#8217; was not declared in this scope
ALSAAudio.cpp:83: error: &#8216;snd_pcm_hw_params_set_access&#8217; was not declared in this scope
ALSAAudio.cpp:84: error: &#8216;SND_PCM_FORMAT_S16_LE&#8217; was not declared in this scope
ALSAAudio.cpp:84: error: &#8216;snd_pcm_hw_params_set_format&#8217; was not declared in this scope
ALSAAudio.cpp:85: error: &#8216;snd_pcm_hw_params_set_rate_near&#8217; was not declared in this scope
ALSAAudio.cpp:86: error: &#8216;snd_pcm_hw_params_set_channels&#8217; was not declared in this scope
ALSAAudio.cpp:87: error: &#8216;snd_pcm_hw_params&#8217; was not declared in this scope
ALSAAudio.cpp:88: error: &#8216;snd_pcm_hw_params_free&#8217; was not declared in this scope
ALSAAudio.cpp:91: error: &#8216;snd_pcm_prepare&#8217; was not declared in this scope
ALSAAudio.cpp:95: error: &#8216;snd_pcm_avail_update&#8217; was not declared in this scope
ALSAAudio.cpp:103: error: &#8216;snd_pcm_readi&#8217; was not declared in this scope
ALSAAudio.cpp:112: error: &#8216;snd_pcm_close&#8217; was not declared in this scope
ALSAAudio.cpp: In constructor &#8216;ALSAOutputPlayer::ALSAOutputPlayer(ALSAAudioOutput*, Player*)&#8217;:
ALSAAudio.cpp:119: error: &#8216;pcm_handle&#8217; was not declared in this scope
ALSAAudio.cpp: In destructor &#8216;virtual ALSAOutputPlayer::~ALSAOutputPlayer()&#8217;:
ALSAAudio.cpp:125: error: &#8216;pcm_handle&#8217; was not declared in this scope
ALSAAudio.cpp:126: error: &#8216;snd_pcm_close&#8217; was not declared in this scope
ALSAAudio.cpp: In member function &#8216;bool ALSAOutputPlayer::playFrames()&#8217;:
ALSAAudio.cpp:137: error: &#8216;pcm_handle&#8217; was not declared in this scope
ALSAAudio.cpp:137: error: &#8216;snd_pcm_avail_update&#8217; was not declared in this scope
ALSAAudio.cpp:140: warning: comparison between signed and unsigned integer expressions
ALSAAudio.cpp:142: error: &#8216;snd_pcm_writei&#8217; was not declared in this scope
ALSAAudio.cpp: In member function &#8216;void ALSAOutputPlayer::initialize()&#8217;:
ALSAAudio.cpp:160: error: &#8216;pcm_handle&#8217; was not declared in this scope
ALSAAudio.cpp:164: error: &#8216;snd_pcm_uframes_t&#8217; was not declared in this scope
ALSAAudio.cpp:164: error: expected `;' before &#8216;period_size&#8217;
ALSAAudio.cpp:165: error: expected `;' before &#8216;buffer_size&#8217;
ALSAAudio.cpp:167: error: &#8216;snd_pcm_hw_params_t&#8217; was not declared in this scope
ALSAAudio.cpp:167: error: &#8216;hw_params&#8217; was not declared in this scope
ALSAAudio.cpp:168: error: &#8216;snd_pcm_sw_params_t&#8217; was not declared in this scope
ALSAAudio.cpp:168: error: &#8216;sw_params&#8217; was not declared in this scope
ALSAAudio.cpp:174: error: &#8216;pcm_handle&#8217; was not declared in this scope
ALSAAudio.cpp:174: error: &#8216;SND_PCM_STREAM_PLAYBACK&#8217; was not declared in this scope
ALSAAudio.cpp:174: error: &#8216;snd_pcm_open&#8217; was not declared in this scope
ALSAAudio.cpp:178: error: &#8216;snd_pcm_hw_params_malloc&#8217; was not declared in this scope
ALSAAudio.cpp:179: error: &#8216;snd_pcm_hw_params_any&#8217; was not declared in this scope
ALSAAudio.cpp:181: error: &#8216;SND_PCM_ACCESS_RW_INTERLEAVED&#8217; was not declared in this scope
ALSAAudio.cpp:181: error: &#8216;snd_pcm_hw_params_set_access&#8217; was not declared in this scope
ALSAAudio.cpp:182: error: &#8216;SND_PCM_FORMAT_S16_LE&#8217; was not declared in this scope
ALSAAudio.cpp:182: error: &#8216;snd_pcm_hw_params_set_format&#8217; was not declared in this scope
ALSAAudio.cpp:183: error: &#8216;snd_pcm_hw_params_set_rate_near&#8217; was not declared in this scope
ALSAAudio.cpp:184: error: &#8216;snd_pcm_hw_params_set_channels&#8217; was not declared in this scope
ALSAAudio.cpp:186: error: &#8216;buffer_size&#8217; was not declared in this scope
ALSAAudio.cpp:186: error: &#8216;snd_pcm_hw_params_set_buffer_size_near&#8217; was not declared in this scope
ALSAAudio.cpp:187: error: &#8216;period_size&#8217; was not declared in this scope
ALSAAudio.cpp:187: error: &#8216;snd_pcm_hw_params_set_period_size_near&#8217; was not declared in this scope
ALSAAudio.cpp:190: error: &#8216;snd_pcm_hw_params&#8217; was not declared in this scope
ALSAAudio.cpp:193: error: &#8216;snd_pcm_hw_params_free&#8217; was not declared in this scope
ALSAAudio.cpp:196: error: &#8216;snd_pcm_sw_params_malloc&#8217; was not declared in this scope
ALSAAudio.cpp:197: error: &#8216;snd_pcm_sw_params_current&#8217; was not declared in this scope
ALSAAudio.cpp:199: error: &#8216;snd_pcm_sw_params_set_start_threshold&#8217; was not declared in this scope
ALSAAudio.cpp:200: error: &#8216;snd_pcm_sw_params_set_avail_min&#8217; was not declared in this scope
ALSAAudio.cpp:202: error: &#8216;snd_pcm_sw_params&#8217; was not declared in this scope
ALSAAudio.cpp:203: error: &#8216;snd_pcm_sw_params_free&#8217; was not declared in this scope
ALSAAudio.cpp:206: error: &#8216;snd_pcm_prepare&#8217; was not declared in this scope
ALSAAudio.cpp:210: error: &#8216;snd_pcm_writei&#8217; was not declared in this scope
ALSAAudio.cpp:212: error: &#8216;snd_pcm_start&#8217; was not declared in this scope
ALSAAudio.cpp: In member function &#8216;virtual void ALSAAudioOutput::run()&#8217;:
ALSAAudio.cpp:261: error: &#8216;class ALSAOutputPlayer&#8217; has no member named &#8216;pcm_handle&#8217;
ALSAAudio.cpp:261: error: &#8216;snd_pcm_poll_descriptors_count&#8217; was not declared in this scope
ALSAAudio.cpp:262: error: &#8216;class ALSAOutputPlayer&#8217; has no member named &#8216;pcm_handle&#8217;
ALSAAudio.cpp:262: error: &#8216;snd_pcm_poll_descriptors&#8217; was not declared in this scope
ALSAAudio.cpp:278: error: &#8216;class ALSAOutputPlayer&#8217; has no member named &#8216;pcm_handle&#8217;
ALSAAudio.cpp:278: error: &#8216;snd_pcm_poll_descriptors_revents&#8217; was not declared in this scope
make[1]: *** [release/ALSAAudio.o] Error 1
make[1]: Leaving directory `/home/main/main/program/mumble-0.9.4'
make: *** [release] Error 2

```

Would be nice if anyone could help me check it out on a amd64 with 64bit arch.

---

### Post by dfreer on 2007-06-10
Install this package for AMD64 and then try compiling it again:
[http://packages.ubuntu.com/feisty/libdevel/libasound2-dev](http://packages.ubuntu.com/feisty/libdevel/libasound2-dev)
If you run into the same error you might need the 32-bit version of that package. If you run into a different error you will need to see what file is causing problems and download either the AMD64 or 32-bit version. You can always post your error messages here if you can't figure them out :)

---

### Post by skatedawe on 2007-06-10
Lovely! Please accept this gift: :popcorn:

I will try it.

Following...

---

### Post by skatedawe on 2007-06-10
Okey, tried it. I think the compilation came a little bit longer too.

Trapped at this following:

```
GlobalShortcut_unix.cpp:36:34: error: X11/extensions/Xevie.h: No such file or directory
GlobalShortcut_unix.cpp: In member function ‘virtual void GlobalShortcutXConfig::accept()’:
GlobalShortcut_unix.cpp:170: warning: declaration of ‘_container_’ shadows a previous local
GlobalShortcut_unix.cpp:164: warning: shadowed declaration is here
GlobalShortcut_unix.cpp: In constructor ‘GlobalShortcutX::GlobalShortcutX()’:
GlobalShortcut_unix.cpp:196: error: ‘XevieQueryVersion’ was not declared in this scope
GlobalShortcut_unix.cpp:203: error: ‘XevieStart’ was not declared in this scope
GlobalShortcut_unix.cpp:208: error: ‘XevieSelectInput’ was not declared in this scope
GlobalShortcut_unix.cpp: In member function ‘void GlobalShortcutX::remap()’:
GlobalShortcut_unix.cpp:253: warning: comparison between signed and unsigned integer expressions
GlobalShortcut_unix.cpp: In member function ‘virtual void GlobalShortcutX::run()’:
GlobalShortcut_unix.cpp:292: warning: use of old-style cast
GlobalShortcut_unix.cpp:292: warning: use of old-style cast
GlobalShortcut_unix.cpp:292: warning: use of old-style cast
GlobalShortcut_unix.cpp:295: warning: use of old-style cast
GlobalShortcut_unix.cpp:298: error: ‘XEVIE_UNMODIFIED’ was not declared in this scope
GlobalShortcut_unix.cpp:298: error: ‘XevieSendEvent’ was not declared in this scope
GlobalShortcut_unix.cpp:337: error: ‘XevieEnd’ was not declared in this scope
make[1]: *** [release/GlobalShortcut_unix.o] Error 1
make[1]: Leaving directory `/home/main/main/program/mumble-0.9.4'
make: *** [release] Error 2

```

---

### Post by skatedawe on 2007-06-10
I will try installing following packages, too see if it solves the problem:

sudo apt-get install libxcb-xevie0 libxcb-xevie0-dbg libxcb-xevie0-dev libxevie-dev libxevie1 libxevie1-dbg

---

### Post by skatedawe on 2007-06-10
yeah. Got it to work. :D

---

### Post by dfreer on 2007-06-10
glad it works! next time though, make sure to read the how-to as it tells you what programs to install:
> Linux pre-requisites
====================

Mumble needs libasound2 (the ALSA developer libraries) as well as the developer
libraries for Xevie.

---

### Post by xanas3712 on 2008-01-13
I did read the howto, and have those libraries installed along with speex-dev, libpulse-dev, etc. which it doesn't list, and I still get errors, here's where it dies... (right at the end while linking it looks like... arg)

```

g++ -L../../debug -o ../../debug/mumble debug/BanEditor.o debug/ACLEditor.o debug/Log.o debug/AudioConfigDialog.o debug/AudioStats.o debug/AudioInput.o debug/AudioOutput.o debug/main.o debug/MainWindow.o debug/ServerHandler.o debug/About.o debug/ConnectDialog.o debug/Settings.o debug/Database.o debug/VersionCheck.o debug/Global.o debug/PlayerModel.o debug/Audio.o debug/ConfigDialog.o debug/Plugins.o debug/LookConfig.o debug/Overlay.o debug/AudioWizard.o debug/ViewCert.o debug/Messages.o debug/TextMessage.o debug/GlobalShortcut.o debug/ACL.o debug/Group.o debug/Channel.o debug/Message.o debug/Connection.o debug/Player.o debug/Timer.o debug/CryptState.o debug/DBus.o debug/ALSAAudio.o debug/GlobalShortcut_unix.o debug/TextToSpeech_unix.o debug/Overlay_unix.o debug/OSS.o debug/PulseAudio.o debug/moc_BanEditor.o debug/moc_ACLEditor.o debug/moc_Log.o debug/moc_AudioConfigDialog.o debug/moc_AudioStats.o debug/moc_AudioInput.o debug/moc_AudioOutput.o debug/moc_MainWindow.o debug/moc_ServerHandler.o debug/moc_About.o debug/moc_ConnectDialog.o debug/moc_GlobalShortcut.o debug/moc_TextToSpeech.o debug/moc_Database.o debug/moc_VersionCheck.o debug/moc_PlayerModel.o debug/moc_ConfigDialog.o debug/moc_Plugins.o debug/moc_LookConfig.o debug/moc_Overlay.o debug/moc_AudioWizard.o debug/moc_ViewCert.o debug/moc_TextMessage.o debug/moc_ACL.o debug/moc_Channel.o debug/moc_Connection.o debug/moc_Player.o debug/moc_DBus.o debug/moc_ALSAAudio.o debug/moc_GlobalShortcut_unix.o debug/moc_OSS.o debug/moc_PulseAudio.o debug/qrc_mumble.o    -L/usr/lib -L/usr/X11R6/lib -lspeex -lssl -lcrypto -lXevie -lasound -lQtDBus -lpthread -lQtSql -lQtXml -lQtOpenGL -lQtGui -lQtNetwork -lQtCore -lGLU -lGL
debug/PulseAudio.o: In function `PulseAudioSystem::query()':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:449: undefined reference to `pa_context_get_server_info'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:449: undefined reference to `pa_operation_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:450: undefined reference to `pa_context_get_sink_info_list'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:450: undefined reference to `pa_operation_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:451: undefined reference to `pa_context_get_source_info_list'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:451: undefined reference to `pa_operation_unref'
debug/PulseAudio.o: In function `PulseAudioSystem::contextCallback(pa_context*)':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:456: undefined reference to `pa_context_get_state'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:464: undefined reference to `pa_context_errno'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:464: undefined reference to `pa_strerror'
debug/PulseAudio.o: In function `PulseAudioSystem::eventCallback(pa_mainloop_api*, pa_defer_event*)':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:145: undefined reference to `pa_stream_get_state'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:155: undefined reference to `pa_stream_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:156: undefined reference to `pa_stream_new'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:157: undefined reference to `pa_stream_set_state_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:158: undefined reference to `pa_stream_set_write_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:177: undefined reference to `pa_stream_disconnect'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:189: undefined reference to `pa_stream_connect_playback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:195: undefined reference to `pa_stream_get_state'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:205: undefined reference to `pa_stream_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:207: undefined reference to `pa_stream_new'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:208: undefined reference to `pa_stream_set_state_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:209: undefined reference to `pa_stream_set_read_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:227: undefined reference to `pa_stream_disconnect'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:236: undefined reference to `pa_stream_connect_record'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:243: undefined reference to `pa_stream_get_state'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:253: undefined reference to `pa_stream_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:255: undefined reference to `pa_stream_new'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:256: undefined reference to `pa_stream_set_state_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:257: undefined reference to `pa_stream_set_read_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:275: undefined reference to `pa_stream_disconnect'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:284: undefined reference to `pa_stream_connect_record'
debug/PulseAudio.o: In function `PulseAudioSystem::run()':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:119: undefined reference to `pa_mainloop_run'
debug/PulseAudio.o: In function `PulseAudioSystem::wakeup()':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:112: undefined reference to `pa_mainloop_get_api'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:114: undefined reference to `pa_mainloop_wakeup'
debug/PulseAudio.o: In function `PulseAudioSystem::write_callback(pa_stream*, unsigned long, void*)':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:428: undefined reference to `pa_stream_write'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:438: undefined reference to `pa_stream_write'
debug/PulseAudio.o: In function `PulseAudioSystem::read_callback(pa_stream*, unsigned long, void*)':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:349: undefined reference to `pa_stream_peek'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:356: undefined reference to `pa_stream_drop'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:412: undefined reference to `pa_stream_drop'
debug/PulseAudio.o: In function `PulseAudioSystem::stream_callback(pa_stream*, void*)':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:334: undefined reference to `pa_stream_get_state'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:336: undefined reference to `pa_stream_get_context'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:336: undefined reference to `pa_context_errno'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:336: undefined reference to `pa_strerror'
debug/PulseAudio.o: In function `~PulseAudioSystem':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:103: undefined reference to `pa_mainloop_quit'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:106: undefined reference to `pa_context_disconnect'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:107: undefined reference to `pa_context_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:108: undefined reference to `pa_mainloop_free'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:103: undefined reference to `pa_mainloop_quit'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:106: undefined reference to `pa_context_disconnect'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:107: undefined reference to `pa_context_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:108: undefined reference to `pa_mainloop_free'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:103: undefined reference to `pa_mainloop_quit'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:106: undefined reference to `pa_context_disconnect'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:107: undefined reference to `pa_context_unref'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:108: undefined reference to `pa_mainloop_free'
debug/PulseAudio.o: In function `PulseAudioSystem':
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:86: undefined reference to `pa_mainloop_new'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:87: undefined reference to `pa_mainloop_get_api'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:89: undefined reference to `pa_context_new'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:90: undefined reference to `pa_context_set_state_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:91: undefined reference to `pa_context_connect'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:86: undefined reference to `pa_mainloop_new'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:87: undefined reference to `pa_mainloop_get_api'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:89: undefined reference to `pa_context_new'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:90: undefined reference to `pa_context_set_state_callback'
/home/xanas/Desktop/mumble-1.1.1/src/mumble/PulseAudio.cpp:91: undefined reference to `pa_context_connect'
collect2: ld returned 1 exit status
make[2]: *** [../../debug/mumble] Error 1
make[2]: Leaving directory `/home/xanas/Desktop/mumble-1.1.1/src/mumble'
make[1]: *** [debug] Error 2
make[1]: Leaving directory `/home/xanas/Desktop/mumble-1.1.1/src/mumble'
make: *** [sub-src-mumble-make_default] Error 2

```

Any ideas?

---

