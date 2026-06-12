---
title: "no sound in games"
date: 2005-11-03
forum: Multimedia &amp; Video
---

### Post by porsher_puddles on 2005-11-03
i am new to linux, so keep things simple please !
The problem
sound works fine playing music, system sounds, but i can't get any sound from games like frozen bubble etc.

My operating system is ubuntu hoary, my sound card is inbuilt in windows its detected as a realtek ac97

What i have tried so fari have been into system -preferences-multimedia system selector, when i run the sound test on default sink i hear sound no worriewhen i run the sound test on default source i get no sound, i hav tried every available option in there but still nothing.
Ok so then i go to the realtek site and download the driver for linux which is realtek linux audion pack, i follow instructions on how to unzip from another post, that all go's ok, then i read the how to install file in the realtek directory basically for automatic installation its just ./install  off it go's installing then i get this
fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep.lo -MD -MP -MF .deps/hwdep.Tpo -c hwdep.c  -fPIC -DPIC -o .libs/hwdep.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep_hw.lo -MD -MP -MF ".deps/hwdep_hw.Tpo" \  -c -o hwdep_hw.lo `test -f 'hwdep_hw.c' || echo './'`hwdep_hw.c; \
then mv -f ".deps/hwdep_hw.Tpo" ".deps/hwdep_hw.Plo"; \
else rm -f ".deps/hwdep_hw.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep_hw.lo -MD -MP -MF .deps/hwdep_hw.Tpo -c hwdep_hw.c  -fPIC -DPIC -o .libs/hwdep_hw.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT hwdep_symbols.lo -MD -MP -MF ".deps/hwdep_symbols.Tpo" \
  -c -o hwdep_symbols.lo `test -f 'hwdep_symbols.c' || echo './'`hwdep_symbols.c; \
then mv -f ".deps/hwdep_symbols.Tpo" ".deps/hwdep_symbols.Plo"; \
else rm -f ".deps/hwdep_symbols.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT hwdep_symbols.lo -MD -MP -MF .deps/hwdep_symbols.Tpo -c hwdep_symbols.c  -fPIC -DPIC -o .libs/hwdep_symbols.o
/bin/sh ../../libtool --mode=link gcc  -g -O2   -o libhwdep.la   hwdep.lo hwdep_hw.lo hwdep_symbols.lo
ar cru .libs/libhwdep.a .libs/hwdep.o .libs/hwdep_hw.o .libs/hwdep_symbols.o
ranlib .libs/libhwdep.a
creating libhwdep.la
(cd .libs && rm -f libhwdep.la && ln -s ../libhwdep.la libhwdep.la)
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/hwdep'
Making all in seq
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/seq'
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_hw.lo -MD -MP -MF ".deps/seq_hw.Tpo" \
  -c -o seq_hw.lo `test -f 'seq_hw.c' || echo './'`seq_hw.c; \
then mv -f ".deps/seq_hw.Tpo" ".deps/seq_hw.Plo"; \
else rm -f ".deps/seq_hw.Tpo"; exit 1; \
fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_hw.lo -MD -MP -MF .deps/seq_hw.Tpo -c seq_hw.c  -fPIC -DPIC -o .libs/seq_hw.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq.lo -MD -MP -MF ".deps/seq.Tpo" \
  -c -o seq.lo `test -f 'seq.c' || echo './'`seq.c; \
then mv -f ".deps/seq.Tpo" ".deps/seq.Plo"; \
else rm -f ".deps/seq.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq.lo -MD -MP -MF .deps/seq.Tpo -c seq.c  -fPIC -DPIC -o .libs/seq.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_event.lo -MD -MP -MF ".deps/seq_event.Tpo" \
  -c -o seq_event.lo `test -f 'seq_event.c' || echo './'`seq_event.c; \
then mv -f ".deps/seq_event.Tpo" ".deps/seq_event.Plo"; \
else rm -f ".deps/seq_event.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_event.lo -MD -MP -MF .deps/seq_event.Tpo -c seq_event.c  -fPIC -DPIC -o .libs/seq_event.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seqmid.lo -MD -MP -MF ".deps/seqmid.Tpo" \
  -c -o seqmid.lo `test -f 'seqmid.c' || echo './'`seqmid.c; \
then mv -f ".deps/seqmid.Tpo" ".deps/seqmid.Plo"; \
else rm -f ".deps/seqmid.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seqmid.lo -MD -MP -MF .deps/seqmid.Tpo -c seqmid.c  -fPIC -DPIC -o .libs/seqmid.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_midi_event.lo -MD -MP -MF ".deps/seq_midi_event.Tpo" \
  -c -o seq_midi_event.lo `test -f 'seq_midi_event.c' || echo './'`seq_midi_event.c; \
then mv -f ".deps/seq_midi_event.Tpo" ".deps/seq_midi_event.Plo"; \
else rm -f ".deps/seq_midi_event.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_midi_event.lo -MD -MP -MF .deps/seq_midi_event.Tpo -c seq_midi_event.c  -fPIC -DPIC -o .libs/seq_midi_event.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT seq_symbols.lo -MD -MP -MF ".deps/seq_symbols.Tpo" \
  -c -o seq_symbols.lo `test -f 'seq_symbols.c' || echo './'`seq_symbols.c; \
then mv -f ".deps/seq_symbols.Tpo" ".deps/seq_symbols.Plo"; \
else rm -f ".deps/seq_symbols.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT seq_symbols.lo -MD -MP -MF .deps/seq_symbols.Tpo -c seq_symbols.c  -fPIC -DPIC -o .libs/seq_symbols.o
/bin/sh ../../libtool --mode=link gcc  -g -O2   -o libseq.la   seq_hw.lo seq.lo seq_event.lo seqmid.lo seq_midi_event.lo seq_symbols.lo
ar cru .libs/libseq.a .libs/seq_hw.o .libs/seq.o .libs/seq_event.o .libs/seqmid.o .libs/seq_midi_event.o .libs/seq_symbols.o
ranlib .libs/libseq.a
creating libseq.la
(cd .libs && rm -f libseq.la && ln -s ../libseq.la libseq.la)
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/seq'
Making all in instr
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/instr'
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT fm.lo -MD -MP -MF ".deps/fm.Tpo" \
  -c -o fm.lo `test -f 'fm.c' || echo './'`fm.c; \
then mv -f ".deps/fm.Tpo" ".deps/fm.Plo"; \
else rm -f ".deps/fm.Tpo"; exit 1; \
fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT fm.lo -MD -MP -MF .deps/fm.Tpo -c fm.c  -fPIC -DPIC -o .libs/fm.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT simple.lo -MD -MP -MF ".deps/simple.Tpo" \
  -c -o simple.lo `test -f 'simple.c' || echo './'`simple.c; \
then mv -f ".deps/simple.Tpo" ".deps/simple.Plo"; \
else rm -f ".deps/simple.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT simple.lo -MD -MP -MF .deps/simple.Tpo -c simple.c  -fPIC -DPIC -o .libs/simple.o
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT iwffff.lo -MD -MP -MF ".deps/iwffff.Tpo" \
  -c -o iwffff.lo `test -f 'iwffff.c' || echo './'`iwffff.c; \
then mv -f ".deps/iwffff.Tpo" ".deps/iwffff.Plo"; \
else rm -f ".deps/iwffff.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT iwffff.lo -MD -MP -MF .deps/iwffff.Tpo -c iwffff.c  -fPIC -DPIC -o .libs/iwffff.o
/bin/sh ../../libtool --mode=link gcc  -g -O2   -o libinstr.la   fm.lo simple.lo iwffff.lo
ar cru .libs/libinstr.a .libs/fm.o .libs/simple.o .libs/iwffff.o
ranlib .libs/libinstr.a
creating libinstr.la
(cd .libs && rm -f libinstr.la && ln -s ../libinstr.la libinstr.la)
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/instr'
Making all in compat
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/compat'
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include     -g -O2 -MT empty.lo -MD -MP -MF ".deps/empty.Tpo" \
  -c -o empty.lo `test -f 'empty.c' || echo './'`empty.c; \
then mv -f ".deps/empty.Tpo" ".deps/empty.Plo"; \
else rm -f ".deps/empty.Tpo"; exit 1; \
fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -g -O2 -MT empty.lo -MD -MP -MF .deps/empty.Tpo -c empty.c  -fPIC -DPIC -o .libs/empty.o
/bin/sh ../../libtool --mode=link gcc  -g -O2   -o libcompat.la   empty.lo
ar cru .libs/libcompat.a .libs/empty.o
ranlib .libs/libcompat.a
creating libcompat.la
(cd .libs && rm -f libcompat.la && ln -s ../libcompat.la libcompat.la)
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/compat'
Making all in conf
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf'
Making all in cards
make[3]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf/cards'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf/cards'
Making all in pcm
make[3]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf/pcm'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf/pcm'
make[3]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf'
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/conf'
Making all in alisp
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/alisp'
if /bin/sh ../../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include    -g -O2 -MT alisp.lo -MD -MP -MF ".deps/alisp.Tpo" \
  -c -o alisp.lo `test -f 'alisp.c' || echo './'`alisp.c; \
then mv -f ".deps/alisp.Tpo" ".deps/alisp.Plo"; \
else rm -f ".deps/alisp.Tpo"; exit 1; \
fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../include -I../../include -g -O2 -MT alisp.lo -MD -MP -MF .deps/alisp.Tpo -c alisp.c  -fPIC -DPIC -o .libs/alisp.o
/bin/sh ../../libtool --mode=link gcc  -g -O2   -o libalisp.la   alisp.lo
ar cru .libs/libalisp.a .libs/alisp.o
ranlib .libs/libalisp.a
creating libalisp.la
(cd .libs && rm -f libalisp.la && ln -s ../libalisp.la libalisp.la)
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src/alisp'
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT conf.lo -MD -MP -MF ".deps/conf.Tpo" \
  -c -o conf.lo `test -f 'conf.c' || echo './'`conf.c; \
then mv -f ".deps/conf.Tpo" ".deps/conf.Plo"; \
else rm -f ".deps/conf.Tpo"; exit 1; \
fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT conf.lo -MD -MP -MF .deps/conf.Tpo -c conf.c  -fPIC -DPIC -o .libs/conf.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT confmisc.lo -MD -MP -MF ".deps/confmisc.Tpo" \
  -c -o confmisc.lo `test -f 'confmisc.c' || echo './'`confmisc.c; \
then mv -f ".deps/confmisc.Tpo" ".deps/confmisc.Plo"; \
else rm -f ".deps/confmisc.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT confmisc.lo -MD -MP -MF .deps/confmisc.Tpo -c confmisc.c  -fPIC -DPIC -o .libs/confmisc.o
confmisc.c: In function `snd_func_private_pcm_subdevice':
confmisc.c:889: warning: passing arg 2 of `snd_config_get_pointer' from incompatible pointer type
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT input.lo -MD -MP -MF ".deps/input.Tpo" \
  -c -o input.lo `test -f 'input.c' || echo './'`input.c; \
then mv -f ".deps/input.Tpo" ".deps/input.Plo"; \
else rm -f ".deps/input.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT input.lo -MD -MP -MF .deps/input.Tpo -c input.c  -fPIC -DPIC -o .libs/input.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT output.lo -MD -MP -MF ".deps/output.Tpo" \
  -c -o output.lo `test -f 'output.c' || echo './'`output.c; \
then mv -f ".deps/output.Tpo" ".deps/output.Plo"; \
else rm -f ".deps/output.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT output.lo -MD -MP -MF .deps/output.Tpo -c output.c  -fPIC -DPIC -o .libs/output.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT async.lo -MD -MP -MF ".deps/async.Tpo" \
  -c -o async.lo `test -f 'async.c' || echo './'`async.c; \
then mv -f ".deps/async.Tpo" ".deps/async.Plo"; \
else rm -f ".deps/async.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT async.lo -MD -MP -MF .deps/async.Tpo -c async.c  -fPIC -DPIC -o .libs/async.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT error.lo -MD -MP -MF ".deps/error.Tpo" \
  -c -o error.lo `test -f 'error.c' || echo './'`error.c; \
then mv -f ".deps/error.Tpo" ".deps/error.Plo"; \
else rm -f ".deps/error.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT error.lo -MD -MP -MF .deps/error.Tpo -c error.c  -fPIC -DPIC -o .libs/error.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT dlmisc.lo -MD -MP -MF ".deps/dlmisc.Tpo" \
  -c -o dlmisc.lo `test -f 'dlmisc.c' || echo './'`dlmisc.c; \
then mv -f ".deps/dlmisc.Tpo" ".deps/dlmisc.Plo"; \
else rm -f ".deps/dlmisc.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT dlmisc.lo -MD -MP -MF .deps/dlmisc.Tpo -c dlmisc.c  -fPIC -DPIC -o .libs/dlmisc.o
dlmisc.c: In function `snd_dlobj_cache_cleanup':
dlmisc.c:211: warning: passing arg 1 of `free' discards qualifiers from pointer target type
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT socket.lo -MD -MP -MF ".deps/socket.Tpo" \
  -c -o socket.lo `test -f 'socket.c' || echo './'`socket.c; \
then mv -f ".deps/socket.Tpo" ".deps/socket.Plo"; \
else rm -f ".deps/socket.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT socket.lo -MD -MP -MF .deps/socket.Tpo -c socket.c  -fPIC -DPIC -o .libs/socket.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT shmarea.lo -MD -MP -MF ".deps/shmarea.Tpo" \
  -c -o shmarea.lo `test -f 'shmarea.c' || echo './'`shmarea.c; \
then mv -f ".deps/shmarea.Tpo" ".deps/shmarea.Plo"; \
else rm -f ".deps/shmarea.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT shmarea.lo -MD -MP -MF .deps/shmarea.Tpo -c shmarea.c  -fPIC -DPIC -o .libs/shmarea.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT userfile.lo -MD -MP -MF ".deps/userfile.Tpo" \
  -c -o userfile.lo `test -f 'userfile.c' || echo './'`userfile.c; \
then mv -f ".deps/userfile.Tpo" ".deps/userfile.Plo"; \
else rm -f ".deps/userfile.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT userfile.lo -MD -MP -MF .deps/userfile.Tpo -c userfile.c  -fPIC -DPIC -o .libs/userfile.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include    -g -O2 -MT names.lo -MD -MP -MF ".deps/names.Tpo" \
  -c -o names.lo `test -f 'names.c' || echo './'`names.c; \
then mv -f ".deps/names.Tpo" ".deps/names.Plo"; \
else rm -f ".deps/names.Tpo"; exit 1; \
fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -g -O2 -MT names.lo -MD -MP -MF .deps/names.Tpo -c names.c  -fPIC -DPIC -o .libs/names.o
/bin/sh ../libtool --mode=link gcc  -g -O2 -Wl,--version-script=Versions  -o libasound.la -rpath /usr/lib -version-info 2:0:0 conf.lo confmisc.lo input.lo output.lo async.lo error.lo dlmisc.lo socket.lo shmarea.lo userfile.lo names.lo control/libcontrol.la mixer/libmixer.la ordinary_mixer/libordinarymixer.la pcm/libpcm.la ordinary_pcm/libordinarypcm.la rawmidi/librawmidi.la timer/libtimer.la hwdep/libhwdep.la seq/libseq.la instr/libinstr.la compat/libcompat.la alisp/libalisp.la -lm -ldl -lpthread
gcc -shared  .libs/conf.o .libs/confmisc.o .libs/input.o .libs/output.o .libs/async.o .libs/error.o .libs/dlmisc.o .libs/socket.o .libs/shmarea.o .libs/userfile.o .libs/names.o -Wl,--whole-archive control/.libs/libcontrol.a mixer/.libs/libmixer.a ordinary_mixer/.libs/libordinarymixer.a pcm/.libs/libpcm.a ordinary_pcm/.libs/libordinarypcm.a rawmidi/.libs/librawmidi.a timer/.libs/libtimer.a hwdep/.libs/libhwdep.a seq/.libs/libseq.a instr/.libs/libinstr.a compat/.libs/libcompat.a alisp/.libs/libalisp.a -Wl,--no-whole-archive  -lm -ldl -lpthread  -Wl,--version-script=Versions -Wl,-soname -Wl,libasound.so.2 -o .libs/libasound.so.2.0.0
(cd .libs && rm -f libasound.so.2 && ln -s libasound.so.2.0.0 libasound.so.2)
(cd .libs && rm -f libasound.so && ln -s libasound.so.2.0.0 libasound.so)
creating libasound.la
(cd .libs && rm -f libasound.la && ln -s ../libasound.la libasound.la)
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src'
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/src'
Making all in aserver
make[1]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/aserver'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../src/pcm    -g -O2 -MT aserver.o -MD -MP -MF ".deps/aserver.Tpo" \
  -c -o aserver.o `test -f 'aserver.c' || echo './'`aserver.c; \
then mv -f ".deps/aserver.Tpo" ".deps/aserver.Po"; \
else rm -f ".deps/aserver.Tpo"; exit 1; \
fi
/bin/sh ../libtool --mode=link gcc  -g -O2   -o aserver  aserver.o ../src/libasound.la
mkdir .libs
gcc -g -O2 -o .libs/aserver aserver.o  ../src/.libs/libasound.so -lm -ldl -lpthread
creating aserver
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/aserver'
Making all in alsalisp
make[1]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/alsalisp'
if gcc -DHAVE_CONFIG_H -I. -I. -I../include -I../include -I../src/alisp    -g -O2 -MT alsalisp.o -MD -MP -MF ".deps/alsalisp.Tpo" \
  -c -o alsalisp.o `test -f 'alsalisp.c' || echo './'`alsalisp.c; \
then mv -f ".deps/alsalisp.Tpo" ".deps/alsalisp.Po"; \
else rm -f ".deps/alsalisp.Tpo"; exit 1; \
fi
/bin/sh ../libtool --mode=link gcc  -g -O2   -o alsalisp  alsalisp.o ../src/libasound.la
mkdir .libs
gcc -g -O2 -o .libs/alsalisp alsalisp.o  ../src/.libs/libasound.so -lm -ldl -lpthread
creating alsalisp
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/alsalisp'
Making all in test
make[1]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/test'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/test'
Making all in utils
make[1]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/utils'
make[1]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9'
Making install in doc
make[1]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc'
Making install in pictures
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc/pictures'
make[3]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc/pictures'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc/pictures'
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc/pictures'
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc'
make[3]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc'
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc'
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/doc'
Making install in include
make[1]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/include'
Making install in sound
make[2]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/include/sound'
make[3]: Entering directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/include/sound'
make[3]: Nothing to be done for `install-exec-am'.
/bin/sh ../../mkinstalldirs /usr/include/alsa/sound
 /usr/bin/install -c -m 644 ainstr_fm.h /usr/include/alsa/sound/ainstr_fm.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_fm.h': Permission denied
 /usr/bin/install -c -m 644 ainstr_gf1.h /usr/include/alsa/sound/ainstr_gf1.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_gf1.h': Permission denied
 /usr/bin/install -c -m 644 ainstr_simple.h /usr/include/alsa/sound/ainstr_simple.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_simple.h': Permission denied
 /usr/bin/install -c -m 644 ainstr_iw.h /usr/include/alsa/sound/ainstr_iw.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/ainstr_iw.h': Permission denied
 /usr/bin/install -c -m 644 asound_fm.h /usr/include/alsa/sound/asound_fm.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/asound_fm.h': Permission denied
 /usr/bin/install -c -m 644 hdsp.h /usr/include/alsa/sound/hdsp.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/hdsp.h': Permission denied
 /usr/bin/install -c -m 644 sb16_csp.h /usr/include/alsa/sound/sb16_csp.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/sb16_csp.h': Permission denied
 /usr/bin/install -c -m 644 sscape_ioctl.h /usr/include/alsa/sound/sscape_ioctl.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/sscape_ioctl.h': Permission denied
 /usr/bin/install -c -m 644 emu10k1.h /usr/include/alsa/sound/emu10k1.h
/usr/bin/install: cannot remove `/usr/include/alsa/sound/emu10k1.h': Permission denied
make[3]: *** [install-alsasoundincludeHEADERS] Error 1
make[3]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/include/sound'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/include/sound'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/charles/realtek-linux-audiopack-3.4/alsa-lib-1.0.9/include'
make: *** [install-recursive] Error 1
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux
checking host system type... i686-pc-linux
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS...
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.9... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
rm: cannot remove `/dev/sndstat': Permission denied
ln: `/dev/sndstat': File exists
Remove Folder.....
./install: line 45: alsaconf: command not found
charles@ubuntu:~/realtek-linux-audiopack-3.4$

and it doesn't cure my problem, any ideas?

---

### Post by nystire on 2005-11-05
It looks like a problem with file permissions. Are you doing this as root? If not, run 'sudo -s' and try again.

---

### Post by porsher_puddles on 2005-11-06
nah it still came up with the same

---

