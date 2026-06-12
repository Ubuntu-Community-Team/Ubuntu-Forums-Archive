---
title: "oggenc - Converting FROM flac TO ogg vorbis"
date: 2007-06-26
forum: Multimedia &amp; Video
---

### Post by kahrn on 2007-06-26
Anyone able to help in the way of using oggenc to take a flac file and convert it into a ogg vorbis file? I tried using oggenc, but for some reason it gives an error.

```

kahrn@netboom:~/music/archive/$ oggenc bleh.flac 
ERROR: Input file "bleh.flac" is not a supported format

```

I know for a fact that it is not the flac file itself at fault, as I only just ripped it from a cd using Grip and have tested it. 

Any help is appreciated.

---

### Post by Major_Kong on 2007-06-26
What version of oggenc are you using ?

PS: You should try to use aoTuv pathed version of oggenc, the reults are arguably better.

[http://www.hydrogenaudio.org/forums/index.php?showtopic=15049](http://www.hydrogenaudio.org/forums/index.php?showtopic=15049)

---

### Post by kahrn on 2007-06-26
I am using oggenc version 1.0.2. I read somewhere that support for converting from flac to ogg was not supported in the default build in ubuntu/debian repos. The only solution to that would be compiling vorbis-tools from source and make sure FLAC support is present.

Although when I try and build vorbis-tools, the last messages that i get when running the configure script are:

> configure: WARNING: FLAC and/on OggFLAC libraries or headers missing, oggenc
will NOT be built with FLAC read support.
configure: WARNING: Prerequisites for ogg123 not met, ogg123 will be skipped.
Please ensure that you have POSIX threads, libcurl and libao libraries and
headers present if you would like to build ogg123.


Now I dont mind about ogg123, but the flac read support is important as it could solve the problem. I just cannot find the OggFlac libraries/headers.

As for the aoTUV patched version, I tried the binary out, and it also failed giving the error of invalid input file, just like oggenc did.

**Edit:**
Well, I got it to compile. I just needed a few more packages, which were..
```
sudo apt-get install libflac++-dev libflac++5c2 libflac-dev liboggflac++-dev liboggflac++2c2 liboggflac-dev 
```
These were all found in the ubuntu repositories. Sadly though after compilation and installation it still gave me the same error.

I have attached the ubuntu package incase anyone is able to test the build that I created and see if they got it to convert from FLAC to OGG Vorbis.
If it does manage to then it must be something on my end or something wrong with the flac files themselves, although they do play quite fine.

---

### Post by shamrock_uk on 2007-10-28
This works for me on a fresh gutsy install (after installing the usual flac/ogg packages of course):

```
find . -name *flac -exec oggenc -q 7 {} ;
```

(run it in the same directory as your flac files)

What error messages do you get with that?

---

### Post by sreyan on 2007-12-21
I was searching for the same solution. I came across this: It is working for me quite well with a large FLAC collection.

[http://osdir.com/ml/multimedia.ogg.vorbis.general/2005-08/msg00006.html](http://osdir.com/ml/multimedia.ogg.vorbis.general/2005-08/msg00006.html)

---

