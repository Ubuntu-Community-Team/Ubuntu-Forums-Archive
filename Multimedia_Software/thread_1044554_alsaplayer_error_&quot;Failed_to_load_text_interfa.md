---
title: "alsaplayer error &quot;Failed to load text interface&quot;"
date: 2009-01-19
forum: Multimedia Software
---

### Post by Jelk on 2009-01-19
Hello, relatively new to ubuntu (old UNIX person).  Was trying to get mms up and running on Ubuntu 8.04.1 and it would not work.  Followed it up, and found it to be due to alsaplayer.  Output from alsaplayer -V

Output plugin: ALSA output v1.9.0beta12
Loading reader plugin: HTTP reader v1.3
Loading reader plugin: File reader v1.1
Loading Input plugin: CDDA player v1.2
Loading Input plugin: MikMod player v1.0
Loading Input plugin: Ogg Vorbis player v1.2
Loading Input plugin: WAV player v1.01
Loading Input plugin: libsndfile plugin v0.1
Loading Input plugin: flac player v1.2
Loading Input plugin: MAD MPEG audio plugin v1.01
Failed to load text interface. This is bad (text,text,/usr/lib/alsaplayer)

Read the forum and could not find anything wrong.  It sees both audio cards and they both appear to work fine (can use xine and other programs to get to them).  Anyone know where to go from here?

Additional info at [http://www.alsa-project.org/db/?f=819a1ca85cd81d375e9487f887ea30e990139ddc](http://www.alsa-project.org/db/?f=819a1ca85cd81d375e9487f887ea30e990139ddc)

FIXED: something must have de-installed the libtext_interface components, needed to apt-get install alsplayer_text

---

### Post by xrae on 2009-09-07
Thanks for figuring that one out -- i've been having the same issue ("Failed to load interface text") and was completely unable to find the solution (the man page for my version (alsaplayer 0.99.80-rc4) doesn't even indicate that the interface name is "text"!).  was trying to find a decent jack-enabled commandline audioplayer suitable for previewing lots of short sounds, and now i think i have it...

---

### Post by sdaau on 2010-12-27
Just another thanks for figuring this out - in Lucid it it 'sudo apt-get install alsaplayer-text'...  Mow I can happilly run
```

alsaplayer -i text -S loop.wav

```

to get a command-line loop player (although the loop is, unfortunately, not seamless - there's like a half second pause). 

Cheers!

---

