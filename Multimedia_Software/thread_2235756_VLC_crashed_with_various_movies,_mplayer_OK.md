---
title: "VLC crashed with various movies, mplayer OK"
date: 2014-07-22
forum: Multimedia Software
---

### Post by sanderj on 2014-07-22
VLC crashes on a lot of movies, one or two seconds into the movie. Strangely enough, mplayer has no problems playing the same movies.

With the standard VLC on Ubuntu 14.04:

```
$ time vlc movie.mwv 
VLC media player 2.1.4 Rincewind (revision 2.1.4-0-g2a072be)
[0x179d058] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
Fontconfig warning: FcPattern object size does not accept value "0"
[0x7f3ab8001248] main vout display error: Failed to resize display
[0x7f3acc0009b8] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0x7f3acc0009b8] main input error: ES_OUT_RESET_PCR called
[vc1 @ 0x7f3ac4c624a0] warning: first frame is no keyframe
Segmentation fault
```

real	0m2.101s
user	0m0.644s
sys	0m0.186s

Same crashes with the PPA version:

```
$ sudo add-apt-repository  ppa:videolan/master-daily
$ sudo apt-get update && sudo apt-get upgrade

$ time vlc movie.mwv 
VLC media player 3.0.0-git Vetinari (revision 2.2.0~~git20140722+r57374+123~ubuntu14.04.1)
[00000000013e9058] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[00007f1dec0009b8] core input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[00007f1dec0009b8] core input error: ES_OUT_RESET_PCR called
[vc1 @ 0x7f1de8c65300] warning: first frame is no keyframe
Segmentation fault

real	0m0.930s
user	0m0.523s
sys	0m0.290s

```

Tips how to proceed?

---

