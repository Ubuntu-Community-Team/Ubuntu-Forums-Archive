---
title: "Audacity - change tempo - plugin required?"
date: 2008-03-21
forum: Multimedia &amp; Video
---

### Post by Sslaxx on 2008-03-21
After needing to do a reinstall of Ubuntu, I find the "Change Tempo" command in Audacity is missing! Does anybody know whyso and what I need to do/install to rectify this?

---

### Post by Holonet on 2008-04-12
After a couple hours, which I found surprisingly fast for this type of problem for me, I have figured this out, I think.

The reason for this is the developers of audacity decided to use system libraries instead of local for some of the dependencies, one of them being soundtouch.  Soundtouch is the library responsible for the change tempo/pitch features.  Unfortunately, even if you compile Audacity from source, it will not see the soundtouch library even if you had it, because the developer only wrote the config to detect version 1.31.  Even Hardy does not have it this updated.

So in short, what you have to do is download the newest soundtouch library from source, you can get it here:

[http://www.surina.net/soundtouch/index.html#download](http://www.surina.net/soundtouch/index.html#download)

You must have automake 1.9...the library looks for 1.9 or it just sits there and spits errors at you.  Compile that, then compile audacity from source.

---

### Post by devnulljp on 2008-04-27
> **Holonet said:**
> After a couple hours, which I found surprisingly fast for this type of problem for me, I have figured this out, I think.

The reason for this is the developers of audacity decided to use system libraries instead of local for some of the dependencies, one of them being soundtouch.  Soundtouch is the library responsible for the change tempo/pitch features.  Unfortunately, even if you compile Audacity from source, it will not see the soundtouch library even if you had it, because the developer only wrote the config to detect version 1.31.  Even Hardy does not have it this updated.

So in short, what you have to do is download the newest soundtouch library from source, you can get it here:

[http://www.surina.net/soundtouch/index.html#download](http://www.surina.net/soundtouch/index.html#download)

You must have automake 1.9...the library looks for 1.9 or it just sits there and spits errors at you.  Compile that, then compile audacity from source.
OK, installed automake 1.9, compiled and installed soundtouch.
Do Ineed to link in those libs anywhere? 
When I try to compile audacity I get these errors:

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
configure: Determining what libraries are available in this tree and on the system
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SNDFILE... no
configure: Libsndfile libraries are NOT available as system libraries
checking for ./lib-src/libsndfile/src/sndfile.h.in... no
configure: libsndfile libraries are NOT available in this source tree
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for XML_ParserCreate in -lexpat... yes
checking expat.h usability... yes
checking expat.h presence... yes
checking for expat.h... yes
configure: Expat libraries are available as system libraries
checking for ./lib-src/expat/xmlparse/xmlparse.h... yes
configure: Expat libraries are available in the local tree
checking for SAMPLERATE... no
configure: Libsamplerate libraries are NOT available as system libraries
checking for ./lib-src/libsamplerate/src/samplerate.h... no
configure: libsamplerate libraries are NOT available in the local tree
checking for ./lib-src/libresample/include/libresample.h... yes
configure: libresample libraries are available in the local tree
checking for vorbis_bitrate_addblock in -lvorbisfile... yes
checking vorbis/vorbisfile.h usability... yes
checking vorbis/vorbisfile.h presence... yes
checking for vorbis/vorbisfile.h... yes
configure: Vorbis libraries are available as system libraries
checking for ./lib-src/libvorbis/include/vorbis/vorbisenc.h... no
checking for ./lib-src/libogg/include/ogg/ogg.h... no
configure: Vorbis libraries are NOT available in this source tree
checking for LIBMAD... no
checking for mad_decoder_init in -lmad... no
configure: libmad libraries are NOT available as system libraries
checking for ./lib-src/libmad/frame.h... no
configure: libmad libraries are NOT available in the local tree
checking for FLAC__stream_decoder_new in -lFLAC... no
checking FLAC/format.h usability... no
checking FLAC/format.h presence... no
checking for FLAC/format.h... no
configure: FLAC/FLAC++ libraries are NOT available as system libraries
checking for ./lib-src/libflac/include/FLAC/format.h... no
checking for ./lib-src/libflac/include/FLAC++/decoder.h... no
configure: FLAC libraries are NOT available in this source tree
checking for id3_file_open in -lid3tag... no
checking id3tag.h usability... no
checking id3tag.h presence... no
checking for id3tag.h... no
configure: Libid3tag libraries are NOT available as system libraries
checking for ./lib-src/libid3tag/frame.h... no
configure: libid3tag libraries are NOT available in the local tree
checking for SOUNDTOUCH... yes
configure: Libsoundtouch libraries are available as system libraries
checking for ./lib-src/soundtouch/include/SoundTouch.h... no
configure: libsoundtouch libraries are NOT available in the local tree
checking for ./lib-src/libnyquist/nyx/nyx.h... yes
configure: nyquist libraries are available in the local tree
checking for VAMP... no
configure: Vamp libraries are NOT available as system libraries
checking for ./lib-src/libvamp/vamp-sdk/hostext/PluginLoader.h... yes
configure: Vamp libraries are available in the local tree
checking for LIBTWOLAME... no
configure: Libtwolame library NOT available as system library
checking for ./lib-src/twolame/libtwolame/twolame.h... no
configure: libtwolame library is NOT available in the local tree
configure: Figuring out what libraries to enable
configure: Using SYSTEM libraries for LIBVORBIS
configure: disabling LIBMAD
configure: disabling LIBSNDFILE
configure: disabling LIBFLAC
configure: disabling LIBID3TAG
configure: disabling LIBSAMPLERATE
configure: Using LOCAL libraries for LIBRESAMPLE
configure: Using SYSTEM libraries for LIBSOUNDTOUCH
configure: Using LOCAL libraries for LIBNYQUIST
configure: Using LOCAL libraries for LIBVAMP
configure: Using SYSTEM libraries for LIBEXPAT
configure: disabling LIBTWOLAME
configure: error: Audacity requires libsndfile to be enabled

---

### Post by faust99 on 2008-04-28
I could not be bothered compiling anything so just downgraded to Audacity 1.3.3. Package is available here [http://packages.ubuntu.com/gutsy/i386/audacity/download](http://packages.ubuntu.com/gutsy/i386/audacity/download) and works in hardy.

---

### Post by Holonet on 2008-04-29
Your configure found soundtouch, so you got the tough part right.  It says right there it needs libsndfile to continue.  You can just install that from Synaptic.  Make sure you install the dev files too.  Whenever you compile something, you want the dev package as well.

---

### Post by mikebela777 on 2008-05-10
I've built the packages. You can download them:

- the new version of audacity (1.3.5 instead of 1.3.4) with soundtouch and twolame support:
[http://www.4shared.com/dir/6982805/bcc2680c/audacity.html](http://www.4shared.com/dir/6982805/bcc2680c/audacity.html)

- the new soundtouch packages (libsoundtouch1c2, libsoundtouch1-dev, soundstretch):
[http://www.4shared.com/dir/6982777/16d1d8da/soundtouch.html](http://www.4shared.com/dir/6982777/16d1d8da/soundtouch.html)

---

### Post by tizo_rh on 2008-05-28
Thanks a lot mikebela777!!! They work perfect in Hardy Heron.

:guitar:

---

### Post by Gyrotwister on 2008-06-30
Mikebela777, you're a life saver!! Works very nicely on my Ubuntu8.04

---

### Post by le1232 on 2008-07-17
> **mikebela777 said:**
> I've built the packages. You can download them:

- the new version of audacity (1.3.5 instead of 1.3.4) with soundtouch and twolame support:
[http://www.4shared.com/dir/6982805/bcc2680c/audacity.html](http://www.4shared.com/dir/6982805/bcc2680c/audacity.html)

- the new soundtouch packages (libsoundtouch1c2, libsoundtouch1-dev, soundstretch):
[http://www.4shared.com/dir/6982777/16d1d8da/soundtouch.html](http://www.4shared.com/dir/6982777/16d1d8da/soundtouch.html)

:( i tried to download this files but the package installer report an error-wrong architecture i386
how can i fix the problem?

---

### Post by bucketoftruth on 2008-07-21
That fixed the tempo change missing from audacity problem, but now there's no sound in Audacity (or flash for that matter)!  I've had this happen before and I fixed it by reinstalling the OS, which I'm not going to do this time.  Any thoughts?

---

