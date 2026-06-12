---
title: "Problem compiling ffmpeg with amr audio encoding"
date: 2008-08-13
forum: Multimedia Software
---

### Post by steviefordi on 2008-08-13
I have had a problem where no media player seems to want to play sound on videos taken from my mobile phone. I've narrowed the problem down to ffmpeg not supporting amr audio encoding.

I have been trying to compile ffmpeg with amr enabled unsuccessfully for some time now. I installed libamrnb and libamrwb from the source on penguin.cz. I then got the ffmpeg source from the gutsy repositories, put the amr source into the sub-directories of ffmpeg/libavcodec/ that the amr.c file requires and configured like so:

```
./configure --disable-static --enable-shared --enable-gpl --enable-pp --enable-liba52 --enable-libdts --enable-dc1394 --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-amr_nb --enable-amr_wb --disable-debug --enable-xvid
```

In the terminal everything seems OK at this point, but make fails with a message about "undefined block_size". On examing ffmpeg's configure.err file I see this at the bottom:

```
gcc -fomit-frame-pointer -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -c -o /tmp/ffmpeg-conf--14357-.o /tmp/ffmpeg-conf--14357-.c
gcc -Wl,--warn-common -rdynamic -export-dynamic -Wl,--as-needed -Wl,-rpath-link,\$(BUILD_ROOT)/libavcodec -Wl,-rpath-link,\$(BUILD_ROOT)/libavformat -Wl,-rpath-link,\$(BUILD_ROOT)/libavutil -o /tmp/ffmpeg-conf--14357- /tmp/ffmpeg-conf--14357-.o -lm -lz -la52 -ldts -lm -lgsm -lmp3lame -lm -ltheora -logg -lvorbis -lvorbisenc -logg -logg -lxvidcore -ldc1394_control -lraw1394 -lfaac -lfaad -ldl
check_cc
BEGIN /tmp/ffmpeg-conf--14357-.c
     1	asm (".align 3");
END /tmp/ffmpeg-conf--14357-.c
gcc -fomit-frame-pointer -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3 -c -o /tmp/ffmpeg-conf--14357-.o /tmp/ffmpeg-conf--14357-.c
/tmp/ccwGCTeb.s: Assembler messages:
/tmp/ccwGCTeb.s:3: Error: alignment not a power of 2

```

Just to clarify I'm using Gutsy (7.10), and if I configure ffmpeg with just the default options it compiles and installs fine.

Any help would be greatly appreciated....

---

### Post by kostkon on 2008-08-13
> **steviefordi said:**
> I have had a problem where no media player seems to want to play sound on videos taken from my mobile phone. I've narrowed the problem down to ffmpeg not supporting amr audio encoding.

I have been trying to compile ffmpeg with amr enabled unsuccessfully for some time now. I installed libamrnb and libamrwb from the source on penguin.cz. I then got the ffmpeg source from the gutsy repositories, put the amr source into the sub-directories of ffmpeg/libavcodec/ that the amr.c file requires and configured like so:

```
./configure --disable-static --enable-shared --enable-gpl --enable-pp --enable-liba52 --enable-libdts --enable-dc1394 --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libogg --enable-libtheora --enable-libvorbis --enable-amr_nb --enable-amr_wb --disable-debug --enable-xvid
```

In the terminal everything seems OK at this point, but make fails with a message about "undefined block_size". On examing ffmpeg's configure.err file I see this at the bottom:

```
gcc -fomit-frame-pointer -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -c -o /tmp/ffmpeg-conf--14357-.o /tmp/ffmpeg-conf--14357-.c
gcc -Wl,--warn-common -rdynamic -export-dynamic -Wl,--as-needed -Wl,-rpath-link,\$(BUILD_ROOT)/libavcodec -Wl,-rpath-link,\$(BUILD_ROOT)/libavformat -Wl,-rpath-link,\$(BUILD_ROOT)/libavutil -o /tmp/ffmpeg-conf--14357- /tmp/ffmpeg-conf--14357-.o -lm -lz -la52 -ldts -lm -lgsm -lmp3lame -lm -ltheora -logg -lvorbis -lvorbisenc -logg -logg -lxvidcore -ldc1394_control -lraw1394 -lfaac -lfaad -ldl
check_cc
BEGIN /tmp/ffmpeg-conf--14357-.c
     1	asm (".align 3");
END /tmp/ffmpeg-conf--14357-.c
gcc -fomit-frame-pointer -Wdeclaration-after-statement -Wall -Wno-switch -Wdisabled-optimization -Wpointer-arith -Wredundant-decls -Wno-pointer-sign -O3 -c -o /tmp/ffmpeg-conf--14357-.o /tmp/ffmpeg-conf--14357-.c
/tmp/ccwGCTeb.s: Assembler messages:
/tmp/ccwGCTeb.s:3: Error: alignment not a power of 2

```

Just to clarify I'm using Gutsy (7.10), and if I configure ffmpeg with just the default options it compiles and installs fine.

Any help would be greatly appreciated....
No need to compile your own *FFmpeg*! Just install the version of it provided by the [*Medibuntu* repository]("http://medibuntu.org/") that has the support for restricted formats enabled (including *AMR* ;)).

Add this repository to your software sources list (instructions are on its website) and then install *FFmpeg* from *Synaptic* (or terminal, of course).

---

### Post by steviefordi on 2008-08-14
Thanks for the reply.

I had already enabled Medibuntu with no luck. Bizarrely though after posting here I had a medibuntu update message which included some (maybe it was all) of the ffmpeg libraries. After installing these updates, then installing ffmpeg from the repositoires I now have sound :). Haven't had time to check yet but I assume this means I can now convert to other formats and retain the sound.

Not sure if this had something to do with me installing libamrnb and libamrwb from source gotten from penguin.cz.

As a newbie, if nothing else I've learnt a lot about compiling packages from source. I wouldn't recommend any other newbies start learning to compile with ffmpeg though! I've been a software developer for years (on windows systems) and I'm starting to realise there is so much I don't know!

---

### Post by cor2y on 2008-08-14
The medibuntu version is good enough since its compiled with most restricted codecs.
The reason compiling yours didn't work is because you used the source from the gutsy repos.
If you wish to compile ffmpeg with restricted format like amr etc its best to use the cutting edge svn version which will be better than the vanilla flavor source thats in the ubuntu repos.
Nothing is wrong with the ubuntu ffmpeg source code just that its an older stable version that may or may not support compiling with what you want, in this case amr support.

---

