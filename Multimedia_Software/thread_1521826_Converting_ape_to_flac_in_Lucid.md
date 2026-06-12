---
title: "Converting ape to flac in Lucid"
date: 2010-07-01
forum: Multimedia Software
---

### Post by damnated on 2010-07-01
I'm having a hard time converting ape files to flac. I tried shncov, with ```
shnconv -o flac *.ape
``` to convert a directory of ape files. The error messages I get ```
shnconv: warning: failed to read data from input file using format: [ape]
shnconv:          + you may not have permission to read file: [01.ape]
shnconv:          + arguments may be incorrect for decoder: [mac]
shnconv:          + verify that the decoder is installed and in your PATH
shnconv:          + this file may be unsupported, truncated or corrupt

```mac is not installed, but, if I check the supported formats of shnconv, ape comes up as well: ```
$ shntool -f
shntool 3.0.7 supported file formats:

 format    ext     input    output  description
 ------    ---     -----    ------  -----------
    wav   .wav   shntool   shntool  RIFF WAVE file format
   aiff  .aiff       sox       sox  Audio Interchange File Format
    shn   .shn   shorten   shorten  Shorten low complexity waveform coder
   flac  .flac      flac      flac  Free Lossless Audio Codec
    ape   .ape       mac       mac  Monkey's Audio Compressor
    ofr   .ofr       ofr       ofr  OptimFROG Lossless WAVE Audio Coder
   lpac      -      lpac         -  Lossless Predictive Audio Compression
     wv    .wv  wvunpack   wavpack  WavPack Hybrid Lossless Audio Compression
   alac      -      alac         -  Apple Lossless Audio Codec
     la      -        la         -  Lossless Audio Compresser
    tta   .tta    ttaenc    ttaenc  TTA Lossless Audio Codec
    als   .als    mp4als    mp4als  MPEG-4 Audio Lossless Coding
    tak   .tak      takc      takc  (T)om's lossless (A)udio (K)ompressor
   bonk  .bonk      bonk      bonk  Bonk lossy/lossless audio compressor
    kxs      -     kexis         -  Kexis lossless WAV file compressor
    mkw   .mkw    mkwcon    mkwcon  MKW Audio Compression format
   cust      -         -   shntool  Custom output format module
   term      -         -   shntool  Sends output to the terminal
   null      -         -   shntool  Sends output to /dev/null

```or this list is just of what it could support if every plugin were installed? I'm not entirely sure about this. If this is the case, how can I install mac? Their official site only offers a windows version...

Moving on, however, I have installed soundKonverter as well, and that also says that it supports ape out of the box, yet when browse to a folder of ape files, soundKonverter can not open them. I've tried dragging the folder, opening just files etc. No luck.

Oh, and for the record: the files are not corrupted and they are not read only. They play flawlessly in Deadbeef, and they passed AudioTester as well. The only reason I'm trying to convert them to flac, is that I won't have to change players if I want to listen to these albums. (I'm using Amarok as my primary audio player, which can't play them.)

---

### Post by mc4man on 2010-07-01
You'll need the mac libs, then works quite easily
Ex.
> doug@doug-desktop:~/Music$ shnconv -o flac *.ape
Converting [luckynight.ape] (1:00.36) --> [luckynight.flac] : 100% OK


I have a version I built myself, you can get the source here - last entry on page
[http://debian-multimedia.org/pool/main/m/monkeys-audio/monkeys-audio.php](http://debian-multimedia.org/pool/main/m/monkeys-audio/monkeys-audio.php)

It is also available as 3 packages on that page, you'll need to install 2 of them for shntool - **first** libmac2_3.99u4-b5-0.1 followed by monkeys-audio_3.99u4-b5-0.0
(make sure to use the ver.# above - from feb. 08 2010

Easy to build - if you want just say so, 1 file must be patched though or build will fail, simple to do (/MACLib/APELink.cpp

Also note that the dm build has a shntool patch, whether of value ..?

---

### Post by damnated on 2010-07-01
Thank you, it worked flawlessly after installing those 2 packages.

---

### Post by statmonkey on 2010-07-13
Thank you, that helped me as well.  If you are looking to split the resulting flac into individual tracks you might be interested in [this information as well]("http://www.webupd8.org/2009/04/split-ape-and-flac-files-in-ubuntu-and.html").

---

### Post by shantiq on 2010-07-26
and if you are lazy like me you can simply use the attached deb:KS

---

### Post by chefbodini on 2011-08-06
Works great!  Thanks!

---

### Post by itilious on 2011-08-09
worked for me, TY so much!

---

