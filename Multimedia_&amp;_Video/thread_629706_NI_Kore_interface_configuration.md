---
title: "NI Kore interface configuration"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by Sirven on 2007-12-02
Hi,
I would like to get my USB soundcard working. What is the best way to configure it.
The Sound Panel setting detect it, but no sounds comming out of it. The main message
error I get is Missing the right GStreamer files. Which one could it be ? There is many.
Do I need any other modules ? 
I also tried to configure it with an alsa installation. I can't go through the entire process
without getting an error. The last one said that I could not complete because of All fonctions were not accessing files. Here is more about it :
Thanks.

/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o alsalisp  alsalisp.o ../src/libasound.la 
mkdir .libs
gcc -g -O2 -o .libs/alsalisp alsalisp.o  ../src/.libs/libasound.so -lm -ldl -lpthread
creating alsalisp
make[1]: quittant le répertoire « /usr/src/alsa-lib-1.0.15rc3/alsalisp »
Making all in test
make[1]: entrant dans le répertoire « /usr/src/alsa-lib-1.0.15rc3/test »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /usr/src/alsa-lib-1.0.15rc3/test »
Making all in utils
make[1]: entrant dans le répertoire « /usr/src/alsa-lib-1.0.15rc3/utils »
make[1]: Rien à faire pour « all ».
make[1]: quittant le répertoire « /usr/src/alsa-lib-1.0.15rc3/utils »
make[1]: entrant dans le répertoire « /usr/src/alsa-lib-1.0.15rc3 »
make[1]: Rien à faire pour « all-am ».
make[1]: quittant le répertoire « /usr/src/alsa-lib-1.0.15rc3 »

My configuration : 

Intel Core duo 2.13 Ghz
MainBoard - MSI 945GM3 Series
2000 mb RAM

(Native-Instruments)
Kore interface I
- USB soundcard -

---

