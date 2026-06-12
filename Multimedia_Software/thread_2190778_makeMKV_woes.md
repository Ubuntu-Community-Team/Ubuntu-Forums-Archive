---
title: "makeMKV woes"
date: 2013-11-29
forum: Multimedia Software
---

### Post by Langstracht on 2013-11-29
I have finally gotten around to (try to) install makeMKV.

I used the instructions listed on:

```
http://www.makemkv.com/forum2/viewtopic.php?f=3&t=224
```

the step:

```
make -f makefile.linux
```

on: 

```
makemkv-oss-1.8.6
```

results in the following error:

```
make: *** [out/libmakemkv.so.1.full] Error 1
```

and sure enough in trying to run:

```
makmkvcon
```

I get the error message:

```
error while loading shared libraries: libmakemkv.so.1: cannot open shared object file: No such file or directory
```

It would appear that makeMKV rocks and I would REALLY like to use it.

Can anyone get me over this problem?

Thanks in advance.

---

### Post by TheYetiWakes on 2013-12-04
Hi

I would suggest maybe using the script outlined in the first post here:  [http://www.makemkv.com/forum2/viewtopic.php?f=3&t=5266](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=5266).  Its worked with no problems for me on 3 different setups and installs all the needed dependencies for MakeMKV.  

Goodluck

---

### Post by Langstracht on 2013-12-04
thanks for taking the time to get back to me.

Alas ... it did not work.


I run 2 machines, one with Mint, the other ubuntu.

Got some errors on Mint:

> libffabi/src/audio_convert.c:79:16: note: each undeclared identifier is reported only once for each function it appears in
libffabi/src/audio_convert.c:79:44: error: ‘AV_SAMPLE_FMT_DBLP’ undeclared (first use in this function)
libffabi/src/audio_convert.c: In function ‘set_generic_function’:
libffabi/src/audio_convert.c:332:1: error: ‘AV_SAMPLE_FMT_U8P’ undeclared (first use in this function)
libffabi/src/audio_convert.c:333:1: error: ‘AV_SAMPLE_FMT_S16P’ undeclared (first use in this function)
libffabi/src/audio_convert.c:335:1: error: ‘AV_SAMPLE_FMT_S32P’ undeclared (first use in this function)
libffabi/src/audio_convert.c:336:1: error: ‘AV_SAMPLE_FMT_FLTP’ undeclared (first use in this function)
libffabi/src/audio_convert.c:337:1: error: ‘AV_SAMPLE_FMT_DBLP’ undeclared (first use in this function)
make: *** [out/libmakemkv.so.1.full] Error 1


and then 

libffabi/src/audio_convert.c:79:44: error: ‘AV_SAMPLE_FMT_DBLP’ undeclared (first use in this function)
libffabi/src/audio_convert.c: In function ‘set_generic_function’:
libffabi/src/audio_convert.c:332:1: error: ‘AV_SAMPLE_FMT_U8P’ undeclared (first use in this function)
libffabi/src/audio_convert.c:333:1: error: ‘AV_SAMPLE_FMT_S16P’ undeclared (first use in this function)
libffabi/src/audio_convert.c:335:1: error: ‘AV_SAMPLE_FMT_S32P’ undeclared (first use in this function)
libffabi/src/audio_convert.c:336:1: error: ‘AV_SAMPLE_FMT_FLTP’ undeclared (first use in this function)
libffabi/src/audio_convert.c:337:1: error: ‘AV_SAMPLE_FMT_DBLP’ undeclared (first use in this function)
make: *** [out/libmakemkv.so.1.full] Error 1

****  Installation failed. Aborting package creation.

There may have been more but these are all I saw and could retrieve.

However in ubuntu there were hundreds (or at least dozens).  Far too many to list but the ones I could retrieve are in the attachment for what it may be worth.

Also for what it may be worth Mint was 12 and ubuntu (ONLY) 10.04.

Been holding off upgrading till I get some order restored to the files and them safely "off line".  Maybe the prospect of becoming able to use makemkv will give me the kick in the lower back that I need to expedite the process.

Be great to get it working "now" though ... if there's anything you can do/suggest.

Thanks in advance.

[ATTACH=CONFIG]248336[/ATTACH]

---

