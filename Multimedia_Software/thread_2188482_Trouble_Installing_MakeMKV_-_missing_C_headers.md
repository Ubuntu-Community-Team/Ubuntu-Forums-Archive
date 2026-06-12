---
title: "Trouble Installing MakeMKV - missing C headers"
date: 2013-11-17
forum: Multimedia Software
---

### Post by W-Unit on 2013-11-17
Howdy!

I'm trying to install MakeMKV in order to play a Blu-Ray.

So I download the two archives from the MakeMKV website (which instructs that both archives - designated "bin" and "oss" - should be installed), extract them, and attempt to install them, but apparently, I am missing some C header files that are needed for the install.

The compiler ("make" IS considered a compiler, right?) complains about not being able to find the following headers:
libavcodec/avcodec.h
libavutil/crc.h
libavutil/log.h
libavutil/common.h

My question is, how do I obtain these headers and fix this problem?

Thanks guys!

Here is the output of my attempt at installing MakeMKV:


First install - "bin" package (appears to have worked fine, but I don't know for sure):
```
will@will-01:~/MakeMKV/makemkv-bin-1.8.6$ sudo make -f makefile.linux install
rm -f /usr/bin/makemkvcon
rm -f /usr/bin/mmdtsdec
rm -f /usr/share/MakeMKV/*.mo.gz
install -d /usr/share/MakeMKV
install -d /usr/bin
install -t /usr/bin bin/i386/makemkvcon
install -t /usr/bin bin/i386/mmdtsdec
install -m 644 -t /usr/share/MakeMKV src/share/default.mmcp.xml
install -m 644 -t /usr/share/MakeMKV src/share/flac.mmcp.xml
install -m 644 -t /usr/share/MakeMKV src/share/wdtv.mmcp.xml
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_deu.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_jpn.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_spa.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_ptb.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_dut.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_swe.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_ita.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_chi.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_pol.mo.gz
install -m 644 -t /usr/share/MakeMKV src/share/makemkv_dan.mo.gz
will@will-01:~/MakeMKV/makemkv-bin-1.8.6$

```

... And the second install, the "oss" package. This is the one that seems to be causing problems; there seem to be missing C header files:
```
will@will-01:~/MakeMKV/makemkv-oss-1.8.6$ ls
libabi      libffabi     libmmbd          makefile.linux  msvc     tmp
libdriveio  libmakemkv   License.txt      makefile.win32  out
libebml     libmatroska  makefile.common  makemkvgui      sstring
will@will-01:~/MakeMKV/makemkv-oss-1.8.6$
will@will-01:~/MakeMKV/makemkv-oss-1.8.6$ sudo make -f makefile.linux install
mkdir -p out
gcc -Os -D_GNU_SOURCE -D_linux_ -D_REENTRANT -shared -Wl,-z,defs -oout/libmakemkv.so.1.full -Ilibebml/inc -DEBML_NO_READ -DEBML_STRICT_API -Ilibmatroska/inc \
        -Ilibmakemkv/inc -Isstring/inc -Imakemkvgui/inc -Ilibabi/inc -Ilibffabi/inc \
        libebml/src/EbmlBinary.cpp libebml/src/EbmlContexts.cpp libebml/src/EbmlCrc32.cpp libebml/src/EbmlDate.cpp libebml/src/EbmlDummy.cpp libebml/src/EbmlElement.cpp libebml/src/EbmlFloat.cpp libebml/src/EbmlHead.cpp libebml/src/EbmlMaster.cpp libebml/src/EbmlSInteger.cpp libebml/src/EbmlString.cpp libebml/src/EbmlSubHead.cpp libebml/src/EbmlUInteger.cpp libebml/src/EbmlUnicodeString.cpp libebml/src/EbmlVersion.cpp libebml/src/EbmlVoid.cpp libebml/src/IOCallback.cpp libebml/src/MemIOCallback.cpp  libmatroska/src/FileKax.cpp libmatroska/src/KaxAttached.cpp libmatroska/src/KaxAttachments.cpp libmatroska/src/KaxBlock.cpp libmatroska/src/KaxBlockData.cpp libmatroska/src/KaxChapters.cpp libmatroska/src/KaxCluster.cpp libmatroska/src/KaxClusterData.cpp libmatroska/src/KaxContentEncoding.cpp libmatroska/src/KaxContexts.cpp libmatroska/src/KaxCues.cpp libmatroska/src/KaxCuesData.cpp libmatroska/src/KaxInfo.cpp libmatroska/src/KaxInfoData.cpp libmatroska/src/KaxSeekHead.cpp libmatroska/src/KaxSegment.cpp libmatroska/src/KaxTag.cpp libmatroska/src/KaxTags.cpp libmatroska/src/KaxTrackAudio.cpp libmatroska/src/KaxTrackEntryData.cpp libmatroska/src/KaxTracks.cpp libmatroska/src/KaxTrackVideo.cpp libmatroska/src/KaxVersion.cpp libmakemkv/src/ebmlwrite.cpp libmakemkv/src/libmkv.cpp libmakemkv/src/version.cpp libmakemkv/src/world.cpp  sstring/src/sstring.cpp \
        libabi/src/ossl_aes.c libabi/src/ossl_sha.c libabi/src/ossl_ec.c libabi/src/zlib.c libabi/src/xpat.c libabi/pssl/ec_key.c libabi/pssl/ec_lib.c libabi/pssl/ec_cvt.c libabi/pssl/ec_mult.c libabi/pssl/ecp_mont.c libabi/pssl/ecp_smpl.c libabi/pssl/ecs_ossl.c libabi/pssl/ecs_sign.c libabi/pssl/ecs_vrf.c libabi/src/httplinux.cpp makemkvgui/src/api_linux.cpp libabi/src/sys_linux.c makemkvgui/src/spawn_posix.cpp libffabi/src/ffabi.c libffabi/src/mlp.c libffabi/src/log.c libffabi/src/audio_convert.c \
        -DHAVE_BUILDINFO_H -Itmp \
        -fPIC -Xlinker -dy -Xlinker --version-script=libmakemkv/src/libmakemkv.vers \
        -Xlinker -soname=libmakemkv.so.1 -lc -lstdc++ -lcrypto -lz -lexpat -lavcodec -lavutil -lm
libffabi/src/ffabi.c:22:32: fatal error: libavcodec/avcodec.h: No such file or directory
 #include <libavcodec/avcodec.h>
                                ^
compilation terminated.
libffabi/src/mlp.c:24:27: fatal error: libavutil/crc.h: No such file or directory
 #include <libavutil/crc.h>
                           ^
compilation terminated.
libffabi/src/log.c:29:27: fatal error: libavutil/log.h: No such file or directory
 #include <libavutil/log.h>
                           ^
compilation terminated.
libffabi/src/audio_convert.c:26:30: fatal error: libavutil/common.h: No such file or directory
 #include <libavutil/common.h>
                              ^
compilation terminated.
make: *** [out/libmakemkv.so.1.full] Error 1
will@will-01:~/MakeMKV/makemkv-oss-1.8.6$
```

---

### Post by steeldriver on 2013-11-17
Did you install all the listed dependencies as described here --> [http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224)

```

sudo apt-get install build-essential libc6-dev libssl-dev libexpat1-dev** libavcodec-dev **libgl1-mesa-dev libqt4-dev

```

Unfortunately that link is from 2008 and the libavXXX / ffmpeg stuff may have changed quite a bit in the meantime - but that would at least be a place to start

---

