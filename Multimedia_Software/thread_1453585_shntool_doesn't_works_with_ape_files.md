---
title: "shntool doesn't works with ape files"
date: 2010-04-13
forum: Multimedia Software
---

### Post by WDYSUN on 2010-04-13
Dear forumers

on my Ubuntu Hardy I used to convert aoe files to flac as follows:

```

shntool conv -o flac file_name.ape

```

but on my Ubuntu Karmic I get 

```

shntool [conv]:          + you may not have permission to read file: [file_name.ape]
shntool [conv]:          + arguments may be incorrect for decoder: [mac]
shntool [conv]:          + verify that the decoder is installed and in your PATH
shntool [conv]:          + this file may be unsupported, truncated or corrupt

```


If use soundconverter it works fine, but I like to do this things on the CLI.

Any suggestions?

Pierre

---

### Post by andrew.46 on 2010-08-07
Hi Pierre,

Have you checked that you have all the relevant decoders at your disposal? Easiest way to check this is:

```

andrew@skamandros~$ shntool -f
shntool 3.0.10 supported file formats:

 format    ext     input    output  description
 ------    ---     -----    ------  -----------
    wav   .wav   shntool   shntool  RIFF WAVE file format
   aiff  .aiff       sox       sox  Audio Interchange File Format
    shn   .shn   shorten   shorten  Shorten low complexity waveform coder
**[COLOR="Red"]   flac  .flac      flac      flac  Free Lossless Audio Codec[/COLOR]**
**[COLOR="Red"]    ape   .ape       mac       mac  Monkey's Audio Compressor[/COLOR]**
   alac      -      alac         -  Apple Lossless Audio Codec
    tak   .tak      takc      takc  (T)om's lossless (A)udio (K)ompressor
    ofr   .ofr       ofr       ofr  OptimFROG Lossless WAVE Audio Coder
    tta   .tta    ttaenc    ttaenc  TTA Lossless Audio Codec
    als   .als    mp4als    mp4als  MPEG-4 Audio Lossless Coding
     wv    .wv  wvunpack   wavpack  WavPack Hybrid Lossless Audio Compression
   lpac      -      lpac         -  Lossless Predictive Audio Compression
     la      -        la         -  Lossless Audio Compresser
    mkw   .mkw    mkwcon    mkwcon  MKW Audio Compression format
   bonk  .bonk      bonk      bonk  Bonk lossy/lossless audio compressor
    kxs      -     kexis         -  Kexis lossless WAV file compressor
   cust      -         -   shntool  Custom output format module
   term      -         -   shntool  Sends output to the terminal
   null      -         -   shntool  Sends output to /dev/null

```

Could be an error in the installation of the external encoder *mac* (Monkey's Audio Codec).

All the best,

Andrew

---

### Post by shantiq on 2010-08-10
hi there wydsun

yes you need to install mac first which is the name of the ape codec   attached here

then go back to shntool it will work now
:KS

---

