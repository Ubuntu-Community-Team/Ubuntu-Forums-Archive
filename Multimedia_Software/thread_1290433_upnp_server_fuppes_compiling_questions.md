---
title: "upnp server fuppes compiling questions"
date: 2009-10-13
forum: Multimedia Software
---

### Post by sdowney717 on 2009-10-13
[http://fuppes.ulrich-voelkel.de/](http://fuppes.ulrich-voelkel.de/)

my recommended dependencies are missing a few things
will it work anyway?
going to try streaming to a dsm-320 dlink box


> check minimum dependencies

checking for PCRE... yes
checking for LIBXML... yes
checking for SQLITE3... yes
checking for pthread_create in -lpthread... yes

check recommended dependencies

checking for UUID... no
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for iconv... yes
checking for working iconv... yes
checking for iconv declaration... 
         extern size_t iconv (iconv_t cd, char * *inbuf, size_t *inbytesleft, char * *outbuf, size_t *outbytesleft);

check optional stuff

checking for taglib-config... no
checking for IMAGEMAGICK_WAND... no
checking for EXIV2... no
checking for LIBAVFORMAT... no
checking for LIBAVFORMAT... no
checking for LIBAVFORMAT... no
configure: *** libavformat (FFmpeg) support disabled ***
checking for mpeg4ip-config... no
configure: *** mpeg4ip/libmp4v2 support disabled ***
checking for VORBISFILE... no
checking mpcdec/config_types.h usability... no
checking mpcdec/config_types.h presence... no
checking for mpcdec/config_types.h... no
checking FLAC/file_decoder.h usability... no
checking FLAC/file_decoder.h presence... no
checking for FLAC/file_decoder.h... no
checking FLAC/stream_decoder.h usability... no
checking FLAC/stream_decoder.h presence... no
checking for FLAC/stream_decoder.h... no
checking for simage-config... no
checking for mysql_config... no
checking sys/inotify.h usability... yes
checking sys/inotify.h presence... yes
checking for sys/inotify.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating m4/Makefile
config.status: creating src/Makefile
config.status: creating src/plugins/Makefile
config.status: creating src/windows/Makefile
config.status: creating src/config.h
config.status: executing depfiles commands
config.status: executing libtool commands

  SUMMARY

  audio transcoding plugins
    encoder:
      lame       : no
      twolame    : no
      pcm/wav    : yes
    decoder:
      vorbis     : no
      mpc        : no
      flac       : no
      faad       : no (aac/mp4/m4a)
      mad        : no (mpeg Layer I, II & III)

  video transcoding plugins
    ffmpeg     : disabled

  image conversion/rescaling plugins
    ImageMagick: disabled (Wand C-API)

  audio metadata extraction plugins
    taglib        : disabled (mp3, ogg, flac & mpc)
    mpeg4ip/mp4v2 : disabled (mp4/m4a)

  image metadata extraction plugins
    Exiv2         : disabled
    ImageMagick   : disabled (Wand C-API)
    simage        : disabled (jpeg, png, gif, tiff, rgb, pic, tga, eps)

  video metadata extraction plugins
    libavformat   : disabled

  miscellaneous
    iconv      : enabled (charset conversion)
    uuid       : disabled
    inotify    : enabled

Thanks for using fuppes
please report bugs


perhaps not from the make

> lib/Common/Exception.cpp: In constructor ‘fuppes::Exception::Exception(std::string, int, const char*, ...)’:
lib/Common/Exception.cpp:53: error: ‘vsnprintf’ was not declared in this scope
make[2]: *** [Exception.lo] Error 1
make[2]: Leaving directory `/home/scott2/fuppes-0.640/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/scott2/fuppes-0.640/src'
make: *** [all-recursive] Error 1
scott2@scott2-desktop:~/fuppes-0.640$ 


---

### Post by KillaB7 on 2009-10-24
I had the same issue compiling on Server 9.10.
You can work around the problem by using an earlier gcc.

./configure CC=gcc-4.3 CXX=g++-4.3 --prefix=/usr

I also ended up using an earlier build due to another issue.
[http://sourceforge.net/tracker/?func=detail&aid=2885303&group_id=141999&atid=751213](http://sourceforge.net/tracker/?func=detail&aid=2885303&group_id=141999&atid=751213)

---

### Post by KillaB7 on 2009-10-24
Hmmm, just rebuilt using build 646 and got the following error:
```
[ERROR] no database version information found. remove the fuppes.db and restart fuppes
[ERROR] unable to create database file
```

Removed the fuppes.db file, restarted and now it works.

---

### Post by PorchSong on 2009-11-01
> **KillaB7 said:**
> I had the same issue compiling on Server 9.10.
You can work around the problem by using an earlier gcc.

./configure CC=gcc-4.3 CXX=g++-4.3 --prefix=/usr

I also ended up using an earlier build due to another issue.
[http://sourceforge.net/tracker/?func=detail&aid=2885303&group_id=141999&atid=751213](http://sourceforge.net/tracker/?func=detail&aid=2885303&group_id=141999&atid=751213)

Where are you running the gcc command?  I am trying to compile but am stuck with the 9.10 / fuppes compile error listed in your links.

When I run the ./configure CC=gcc-4.3 CXX=g++-4.3 --prefix=/usr command after I run the "autoreconf -vfi"  I get this readout:

jim@jim-porchsong:~/fuppes$ sudo ./configure CC=gcc-4.3 CXX=g++-4.3 --prefix=/usr
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc-4.3
checking for C compiler default output file name... 
[COLOR="Red"]configure: error: in `/home/jim/fuppes':
configure: error: C compiler cannot create executables[/COLOR]
See `config.log' for more details.

Continuing on with fuppes compile, it get kicked out at src error on make command.  

So, how did you get it to compile?  When and where are you running your "fix" command?  I am beating myself over the head trying to solve this one.  It looks like you licked this one, I can't seem to overcome it.  If you would do a quick compile walkthrough.  Here is what I am doing (assuming all libraries are loaded):

svn co [https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk](https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk) fuppes
cd fuppes/
autoreconf -vfi
./configure --prefix=/usr
make  [COLOR="Red"]<<---kicks out with src error:

lib/Common/Exception.cpp:53: error: ‘vsnprintf’ was not declared in this scope
make[2]: *** [Exception.lo] Error 1
make[2]: Leaving directory `/home/jim/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/jim/fuppes/src'
make: *** [all-recursive] Error 1
[/COLOR]

sudo make install


I am on 9.10 x64 too and installing to my home directory.

---

### Post by sdowney717 on 2009-11-01
> I also ended up using an earlier build due to another issue.
[http://sourceforge.net/tracker/?func...99&atid=751213](http://sourceforge.net/tracker/?func...99&atid=751213)

i think you have to use an older version of fuppes as well!
I ended up using ushare, it works very well

I would like to see a linux version of tversity or playon.

Does anyone know of a linux pnp server that gathers podcast internet content?

---

### Post by KillaB7 on 2009-11-01
Did you install the gcc-4.3 packages?

I used the following commands to build fuppes.  No sudo required until the end.
```

$ svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure CC=gcc-4.3 CXX=g++-4.3 --prefix=/usr
$ make
$ sudo make install

```

Your problem could also be different since I built for x86.

---

### Post by KillaB7 on 2009-11-01
> **sdowney717 said:**
> i think you have to use an older version of fuppes as well!

No, I managed to build 0.646 just fine.

> 
I ended up using ushare, it works very well

I would like to see a linux version of tversity or playon.

Fuppes may be a pain to set up at times, but I still prefer it to any other DLNA software out there.  Once you get it going, it's great.

I've tried TVersity and PS3 Media Server, but always come back to fuppes for it's simplicity.

Does ushare automatically reindex files like fuppes?

> 
Does anyone know of a linux pnp server that gathers podcast internet content?

I'd like to know this as well.  I watch a few Revision3 shows, and would love to know how to download them as soon as they come out.

---

### Post by PorchSong on 2009-11-01
> **KillaB7 said:**
> Did you install the gcc-4.3 packages?

I used the following commands to build fuppes.  No sudo required until the end.
```

$ svn co https://fuppes.svn.sourceforge.net/svnroot/fuppes/trunk fuppes
$ cd fuppes
$ autoreconf -vfi
$ ./configure CC=gcc-4.3 CXX=g++-4.3 --prefix=/usr
$ make
$ sudo make install

```

Your problem could also be different since I built for x86.

I finally got it.  Installed gdd-4.3 and assumed it brought g++-4.3 with it.  Futhermore, I had to do "sudo make" and "sudo make install" to finally get it to go.  Weird, but had to use "sudo" on the make.  Thank you.  Also, I cleaned up my nubie guide and updated it to 9.10 and included your ./config and gave you credit.  Thanks again.  Here is the updated guide:

[http://ubuntuforums.org/showthread.php?t=1310511](http://ubuntuforums.org/showthread.php?t=1310511)

---

### Post by Shhnap on 2009-11-03
This is the wrong way to solve this problem: using compiler hacks. Please see PorchSongs fuppes guide for more: [http://ubuntuforums.org/showthread.php?t=1310511](http://ubuntuforums.org/showthread.php?t=1310511).

---

### Post by sdowney717 on 2009-11-08
[http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217&p=13908&hilit=+366+beta+download#p13908](http://ps3mediaserver.org/forum/viewtopic.php?f=2&t=3217&p=13908&hilit=+366+beta+download#p13908)

this program runs using sun java jre and allows transcoding of web content

and works in linux

---

### Post by Shhnap on 2009-11-08
ps3 media server is very good. Unless you want XBox support; in which case they all seem to be about the same. (Though if your server is not that fast or you want it to be minimal, running the jre on your machine is going to take up some space. You may or may not care though; it's upto you really)

---

### Post by sdowney717 on 2009-11-10
[http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)
This minidlna is better than ushare.
it does automatic folder refreshing without interrupting the upnp serving of currently playing video.

with ushare, placing a file in the shared folder to become visible to the media player, you have to do a reload. then my dsm 320 stops playing the stream and i cant just restart but have to back out of the directory to replay the video.

---

### Post by Shhnap on 2009-11-11
Good point. This is currently on the fuppes TODO list and I think i'll try and implement it myself and send in a patch.

---

### Post by KillaB7 on 2009-11-11
Fuppes already does this.

---

### Post by Shhnap on 2009-11-11
You are right. I just checked and fuppes has inotify support. fuppes ftw.

---

