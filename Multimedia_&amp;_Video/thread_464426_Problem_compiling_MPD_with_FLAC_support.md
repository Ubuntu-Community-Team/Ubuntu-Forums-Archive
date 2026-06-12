---
title: "Problem compiling MPD with FLAC support"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by TorjusH on 2007-06-04
Hello, 

I migrated from windows to ubuntu a while ago, and i am pretty new to a lot of this, but i feel like i am starting to get the hang of some stuff at least, and i must say, ubuntu is really great :) Took a while before i found a music player that i liked, but i have been using mpd for a while, and i must say, it's great! :) 

But recently i have downloaded some flac files, and when i compiled mpd for the first time it was without flac-support, and it worked great, but naturally wont play flac files.

Now im trying to compile it again,  this time with flac support. But i can't really get it to work, i installed the newest flac from source, and all seemed to fine, but still, when i run the configure script for mpd it doesn't seem to find my libflac...

here is some of the output from ./configure:
```
checking for Ogg... yes
checking for Vorbis... yes
checking for libFLAC... no
*** Could not run libFLAC test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding libFLAC or finding the wrong
*** version of libFLAC. If it is not finding libFLAC, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
checking for libOggFLAC... no
*** Could not run libOggFLAC test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means libOggFLAC was incorrectly installed
*** or that you have moved libOggFLAC since it was installed. In the latter case, you
*** may want to edit the libOggFLAC-config script: 
checking for audiofile-config... /usr/bin/audiofile-config
checking for Audio File Library - version >= 0.1.7... yes
checking for libmikmod-config... no
checking for libmikmod - version >= 3.1.7... no
*** The libmikmod-config script installed by libmikmod could not be found
*** If libmikmod was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the LIBMIKMOD_CONFIG environment variable to the
*** full path to libmikmod-config.
configure: creating ./config.status
config.status: creating src/mp4ff/Makefile
config.status: WARNING:  src/mp4ff/Makefile.in seems to ignore the --datarootdir setting
config.status: creating doc/Makefile
config.status: WARNING:  doc/Makefile.in seems to ignore the --datarootdir setting
config.status: creating src/Makefile
config.status: WARNING:  src/Makefile.in seems to ignore the --datarootdir setting
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

########### MPD CONFIGURATION ############

 Playback Support:
 libao support .................disabled
 OSS support ...................enabled
 ALSA support ..................enabled
 Sun support ...................disabled
 OS X support ..................disabled
 PulseAudio support ............disabled
 Media MVP support .............disabled
 Shout streaming support .......disabled

 File Format Support:
 ID3 tag support ...............enabled
 mp3 support ...................enabled
 Ogg Vorbis support ............enabled
   using tremor.................no
 FLAC support ..................disabled
 OggFLAC support ...............disabled
 Wave file support .............enabled
 MP4/AAC support ...............disabled
 Musepack (MPC) support ........disabled
 MOD support ...................disabled

##########################################

You are now ready to compile MPD
Type "make" to compile MPD

```

And if i do a search for libFLAC, i find these files:
```
/usr/lib/libFLAC.so.7.0.0
/usr/lib/libFLAC.so.7
/usr/local/lib/libFLAC.so.8.0.1
/usr/local/lib/libFLAC.so.8
/usr/local/lib/libFLAC.so

```

Anyone have any idea of what to do, and how to do it? :)

Also, im not really sure if this was the right place to post, but didn't really know where else to post it :)

Thank you, 
Torjus

---

### Post by TorjusH on 2007-06-05
I found out that i hadn't installed the flac-dev package, so i installed that from the repos, and also the other flac packages. But it didnt't get me much further, now when running the configure script, all seems to be ok, and it says that flac is enabled, but when i try make, it gives me an error which look like this: 

```
mpd-flac_plugin.o: In function `flac_decode_internal':
/home/torjus/sources/MPD/mpd/src/inputPlugins/flac_plugin.c:361: undefined reference to `FLAC__stream_decoder_init_stream'
/home/torjus/sources/MPD/mpd/src/inputPlugins/flac_plugin.c:354: undefined reference to `FLAC__stream_decoder_init_ogg_stream'
/home/torjus/sources/MPD/mpd/src/inputPlugins/flac_plugin.c:383: undefined reference to `FLAC__stream_decoder_seek_absolute'
mpd-flac_plugin.o: In function `flac_plugin_init':
/home/torjus/sources/MPD/mpd/src/inputPlugins/flac_plugin.c:488: undefined reference to `FLAC_API_SUPPORTS_OGG_FLAC'
mpd-flac_plugin.o: In function `oggflac_tag_dup':
/home/torjus/sources/MPD/mpd/src/inputPlugins/flac_plugin.c:446: undefined reference to `FLAC__metadata_chain_read_ogg'
mpd-flac_plugin.o: In function `flacWrite':
/home/torjus/sources/MPD/mpd/src/inputPlugins/flac_plugin.c:230: undefined reference to `FLAC__stream_decoder_get_decode_position'
collect2: ld returned 1 exit status
make[2]: *** [mpd] Error 1
make[2]: Leaving directory `/home/torjus/sources/MPD/mpd/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/torjus/sources/MPD/mpd/src'
make: *** [install-recursive] Error 1

```

Anyone have any clue why this is happening?

Thanks in advance,
Torjus

---

