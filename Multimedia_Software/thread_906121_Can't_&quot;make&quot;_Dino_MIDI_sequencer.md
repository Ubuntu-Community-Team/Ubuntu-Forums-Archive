---
title: "Can't &quot;make&quot; Dino MIDI sequencer"
date: 2008-08-31
forum: Multimedia Software
---

### Post by whaxx0r on 2008-08-31
I want to use Dino but just can't compile it. It just whines about "too many arguments to function 'POTATO'". What can I do?

```
DING@DONG:~/Ohjelmat/dino-0.2.2$ make
Making all in src
make[1]: Siirrytään hakemistoon "/home/DING/Ohjelmat/dino-0.2.2/src"
make  all-recursive
make[2]: Siirrytään hakemistoon "/home/DING/Ohjelmat/dino-0.2.2/src"
Making all in libdinoseq
make[3]: Siirrytään hakemistoon "/home/DING/Ohjelmat/dino-0.2.2/src/libdinoseq"
if /bin/bash ../../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I../../src  -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include     -DNDEBUG   -g -O2 -MT midibuffer.lo -MD -MP -MF ".deps/midibuffer.Tpo" -c -o midibuffer.lo midibuffer.cpp; \
 then mv -f ".deps/midibuffer.Tpo" ".deps/midibuffer.Plo"; else rm -f ".deps/midibuffer.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I../../src -I/usr/include/libxml++-2.6 -I/usr/lib/libxml++-2.6/include -I/usr/include/libxml2 -I/usr/include/glibmm-2.4 -I/usr/lib/glibmm-2.4/include -I/usr/include/sigc++-2.0 -I/usr/lib/sigc++-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -DNDEBUG -g -O2 -MT midibuffer.lo -MD -MP -MF .deps/midibuffer.Tpo -c midibuffer.cpp  -fPIC -DPIC -o .libs/midibuffer.o
/usr/include/jack/midiport.h: In member function 'unsigned char* Dino::MIDIBuffer::reserve(double, size_t)':
/usr/include/jack/midiport.h:112: error: too many arguments to function 'jack_midi_data_t* jack_midi_event_reserve(void*, jack_nframes_t, size_t)'
midibuffer.cpp:58: error: at this point in file
/usr/include/jack/midiport.h: In member function 'int Dino::MIDIBuffer::write(double, const unsigned char*, size_t)':
/usr/include/jack/midiport.h:131: error: too many arguments to function 'int jack_midi_event_write(void*, jack_nframes_t, const jack_midi_data_t*, size_t)'
midibuffer.cpp:68: error: at this point in file
make[3]: *** [midibuffer.lo] Virhe 1
make[3]: Poistutaan hakemistosta "/home/DING/Ohjelmat/dino-0.2.2/src/libdinoseq"
make[2]: *** [all-recursive] Virhe 1
make[2]: Poistutaan hakemistosta "/home/DING/Ohjelmat/dino-0.2.2/src"
make[1]: *** [all] Virhe 2
make[1]: Poistutaan hakemistosta "/home/DING/Ohjelmat/dino-0.2.2/src"
make: *** [all-recursive] Virhe 1
DING@DONG:~/Ohjelmat/dino-0.2.2$

```Or is there a deb package for Dino?

---

### Post by Category on 2008-11-22
I too am having similar problems getting this sequencer up and running - which is annoying, as it looks PERFECT for my normal workflow.

Has anyone had any success building this on Ubuntu?

---

### Post by larsl on 2008-11-24
Hello, I am the author of Dino.

Someone reported this bug in the Dino [bug tracker]("https://savannah.nongnu.org/bugs/?24913"). I believe I have fixed it, and will get a bugfix release out as soon as someone confirms it. There are test instructions on the tracker page.

If you do test it, please leave a report in the tracker as I don't check back here very often.

---

