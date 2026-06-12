---
title: "problems installing audacity 1.3.3 beta"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by jaskah on 2007-08-12
hello
i just tried to install audacity 1.3.3 beta and got the following error messages during compile:

cc1plus: error: unrecognized command line option "-msse"
make[4]: *** [AAFilter.lo] Error 1
make[4]: Leaving directory `/home/jason/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/source/SoundTouch'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jason/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch/source'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jason/Desktop/audacity-src-1.3.3-beta/lib-src/soundtouch'
make[1]: *** [soundtouch-recursive] Error 2
make[1]: Leaving directory `/home/jason/Desktop/audacity-src-1.3.3-beta/lib-src'
make: *** [audacity] Error 2


does anyone know what could be wrong here?

i´ve already installed the following libraries:

sudo apt-get install build-essential libwxgtk2.8-0 libwxgtk2.8-dev libmad0 libmad0-dev libsndfile1 libsndfile1-dev gettext libwxbase2.6-dev libwxgtk2.6-dev wx2.6-headers libmad0-dev libvorbis-dev libogg-dev libflac-dev libflac++-dev libid3tag0-dev zlib1g-dev libtwolame0 libtwolame-dev libgtk-dev libwxgtk-dev twolame libasound2-dev libjack0.100.0-dev portaudio19-dev libgtk2.0-dev

and i was trying to install like this:

./configure –program-suffix=beta && make
sudo make install

i am using xubuntu feisty on a g4 macintosh powerbook ¨titanium.¨

thanks in advance for any help!

---

