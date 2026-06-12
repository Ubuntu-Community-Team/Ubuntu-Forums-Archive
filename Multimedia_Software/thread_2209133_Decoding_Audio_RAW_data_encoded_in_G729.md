---
title: "Decoding Audio RAW data encoded in G729"
date: 2014-03-04
forum: Multimedia Software
---

### Post by Tanio_Artino on 2014-03-04
Hi all,

I have exported some audio data from an old voice backup which was stored on a magnetic tape (DDS-4 tape).
To accomplish this task I used the dd command and therefore I have now my data in binary code on my disk and I can visualize each voice file in caret notation as follow (3 files examples below) :

r<88>0^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@<9A>w^@^@<E7><AB><E2>@<DC>^@^@^@<CD><CC>1^A<AA>BQ^@z<CC>1^A<DD>4<DA>^@<DF><CC>1^A,;^V^A^B^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@...
r<88>0^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@<DE>/^@^@<E7><AB><E2>@<DC>^@^@^@<CD><CC>1^A<AA>BQ^@i<CC>1^A<98>B<AD>^@<DC><CC>1^A7^^<92>^@^B^@^@^@^@^@^@^@^@^@^@^@^@^@^.....
r<88>0^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@<99>w^@^@<E7><AB><E2>@<DC>^@^@^@<CD><CC>1^A<A3>BQ^@i<CC>1^A<CB>A<AD>^@<CD><CC>1^AJ=O^@^B^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^....

The data shown above has been indexed on the tape using a proprietary software and I do not have this software any more and therefore I am trying to do reverse engineer on the tape to decode it.

An expert of the field told me that the file has been encoded using G729 codecs 

I would like to know how I can go further in the extraction process to be able to listen the data extracted and decode the raw data using this codec

Many Thanks

---

### Post by ajgreeny on 2014-03-04
A quick google for **linux G729 codecs** quickly gave me some possibilities, which I am sure you could have found in about 10 seconds.
[http://www.opentelecoms.org/codecs-open-source-g729-g723.1-asterisk](http://www.opentelecoms.org/codecs-open-source-g729-g723.1-asterisk)
[http://asterisk.hosting.lv/](http://asterisk.hosting.lv/)

---

### Post by Tanio_Artino on 2014-03-04
Of course I looked carefully before posting and if you look the links you posted those drivers are related to the Asterisk open source PBX. 

The first step to install the codec is:

Choose codec binary appropriate for your Asterisk version and CPU type, use x86_64 for 64-bit mode (I do know what Asterisk is)
I was looking to a simple g729 decoder, and I found [this]("http://codecpro.com/openInitG729.html") which unfortunately is not a native solution

I have tried to use wine with this codecs

root@TITANIUM:/home/tanio/Downloads/codec/codecProG729_Experimental# ls
CodecPro_ExperimentalG729.pdf  cp_g729_decoder.exe  cp_g729_encoder.exe  cp_g729.lib  vc110.pdb
cp_g729_decoder.c              cp_g729_encoder.c    cp_g729.h            sample.raw   VS2012_project
root@TITANIUM:/home/tanio/Downloads/codec/codecProG729_Experimental# wine cp_g729_decoder.exe sample.raw sample.pcm
err:module:import_dll Library MSVCR110.dll (which is needed by L"Z:\\home\\tanio\\Downloads\\codec\\codecProG729_Experimental\\cp_g729_decoder.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\tanio\\Downloads\\codec\\codecProG729_Experimental\\cp_g729_decoder.exe" failed, status c0000135

I get this error
However I do not think it is the right direction

---

### Post by andrew.46 on 2014-03-04
> **Tanio_Artino said:**
> An expert of the field told me that the file has been encoded using G729 codecs 

I have to admit I cannot quite see how you are extracting your data but there is an open source decoder for g729:

```

andrew@ilium~$ ffmpeg -codecs | grep -i g729
[...]
**[COLOR="#FF0000"] D.A.L. g729                 G.729[/COLOR]**


```

(D.A.L= Decoder Audio Lossy Compression). So playback should be easy enough but I am not sure how to translate from your tape to playable format :(.

---

### Post by Tanio_Artino on 2014-03-05
Thank you andrew, This is what I am looking for but unfortunately it does not work properly

```
ffmpeg version 0.8.10-4:0.8.10-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Feb  6 2014 20:59:08 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.

```

I have had a look around and installed some libraries but nothing happens
I get the same error with avconv

Any other other open source decoder ?

---

### Post by FakeOutdoorsman on 2014-03-05
You're using an old, fake ffmpeg. I don't know if it, or avconv, can decode G.729. You can download and try a [recent, real build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds):

Download:
```
$ wget http://ffmpeg.gusari.org/static/32bit/ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
```
Extract:
```
$ tar xzvf ffmpeg.static.32bit.$(date -d yesterday +%F).tar.gz
```
Run (notice the **./** before the ffmpeg):
```
$ ./ffmpeg -decoders | grep 729
$ ./ffmpeg -i input output
```

---

