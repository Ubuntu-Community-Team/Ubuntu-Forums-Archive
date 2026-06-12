---
title: "Fuppes Make Errors"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by NicholasLee on 2007-11-06
I have found a couple other threads with similar problems which have not resolved.  I don't mean to weigh down the forum, but perhaps I have some additional information which can reach a solution.

It took some time for me to install fuppes. There were a lot of dependencies, and I had not found a guide before I started. After I finally had it running and configured according to instructions I'd found, it still would not communicate with the device I was using (an Xbox 360). To get it out of the way, I was able to use ushare without any tweaking.

I thought perhaps I had made a mistake in the compiling process, so I decided to remove fuppes and start over. Unfortunately, I had not made the package correctly and had to delete the fuppes directories manually. If there were any files outside of the /fuppes and /.fuppes directories, I missed them.

For my second attempt, I followed the instructions found here: [http://anonymouscoward.org](http://anonymouscoward.org)
After a bit of finoodling, I reached the "make" step. This fails at each attempt. I've tried reinstalling all the packages involved and replacing the files in the /fuppes directory with those from a fresh tarball. This is the entirety of the output after running "make" from the /fuppes directory:

```

Making all in src
make[1]: Entering directory `/home/nicholas/fuppes/src'
if test -e "../version.sh"; then \
                ../version.sh; \
        fi
make  all-am
make[2]: Entering directory `/home/nicholas/fuppes/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib   -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg   -I/usr/include/swscale -I/usr/include/ffmpeg   -I/usr/include/libxml2      -D_FILE_OFFSET_BITS=64    -g -O2   -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c -o FileDetails.lo `test -f 'lib/ContentDirectory/FileDetails.cpp' || echo './'`lib/ContentDirectory/FileDetails.cpp
 g++ -DHAVE_CONFIG_H -I. -I/usr/include/taglib -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/include/swscale -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c lib/ContentDirectory/FileDetails.cpp  -fPIC -DPIC -o .libs/FileDetails.o
lib/ContentDirectory/FileDetails.cpp:40:29: error: wand/MagickWand.h: No such file or directory
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute ignored in declaration of 'struct ImgReSampleContext'
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute for 'struct ImgReSampleContext' must follow the 'struct' keyword
/usr/include/ffmpeg/avcodec.h:2437: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2444: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2448: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2450: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avformat.h:282: warning: 'AVFrac' is deprecated (declared at /usr/include/ffmpeg/avformat.h:118)
lib/ContentDirectory/FileDetails.cpp: In member function 'bool CFileDetails::GetImageDetails(std::string, SImageItem*)':
lib/ContentDirectory/FileDetails.cpp:249: error: 'MagickBooleanType' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:249: error: expected `;' before 'status'
lib/ContentDirectory/FileDetails.cpp:250: error: 'MagickWand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:250: error: 'magick_wand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:252: error: 'NewMagickWand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:253: error: 'status' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:253: error: 'MagickReadImage' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:255: error: 'MagickFalse' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:257: error: 'ExceptionType' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:257: error: expected `;' before 'severity'
lib/ContentDirectory/FileDetails.cpp:259: error: 'severity' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:259: error: 'MagickGetException' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:260: error: 'GetMagickModule' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:261: error: 'MagickRelinquishMemory' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:263: error: 'DestroyMagickWand' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:267: error: 'MagickGetImageWidth' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:268: error: 'MagickGetImageHeight' was not declared in this scope
lib/ContentDirectory/FileDetails.cpp:270: error: 'DestroyMagickWand' was not declared in this scope
make[2]: *** [FileDetails.lo] Error 1
make[2]: Leaving directory `/home/nicholas/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/nicholas/fuppes/src'
make: *** [all-recursive] Error 1

```

Can I salvage the attempt or is fuppes fu... screwed?

---

