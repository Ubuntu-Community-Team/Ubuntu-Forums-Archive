---
title: "Tv tuners"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by mrfishhat on 2006-06-10
Hi, recently I purchased a HD-5500 from pcHDtv because i wanted a linux compatable HD tv tuner card, now sadly i cant get working drivers. the CD that came with the card has some on it, but  they refuse to "make" i keep getting the same error. the output of make is


make -C /home/mrfishhat/Desktop/tv/v4l-dvb/v4l
make[1]: Entering directory `/home/mrfishhat/Desktop/tv/v4l-dvb/v4l'
scripts/make_makefile.pl
creating symbolic links...
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/home/mrfishhat/Desktop/tv/v4l-dvb/v4l  modules
make[2]: Entering directory `/lib/modules/2.6.15-23-386/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.15-23-386/build'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/mrfishhat/Desktop/tv/v4l-dvb/v4l'
make: *** [all] Error 2


this happens every single time.


any ieas?

---

