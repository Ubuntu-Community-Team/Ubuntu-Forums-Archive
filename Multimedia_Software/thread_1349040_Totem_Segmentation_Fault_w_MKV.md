---
title: "Totem Segmentation Fault w/ MKV"
date: 2009-12-07
forum: Multimedia Software
---

### Post by NinjaPablo on 2009-12-07
Totem will just disappear with no error when playing certain MKV files, usually within 1-2 minutes of opening the file. When I start it from the command line, the only error returned is:
```

$ totem
Segmentation fault

```And checking dmesg yields
```

$ sudo dmesg | grep segfault
[87498.155408] totem[17683]: segfault at c ip 0612e5a6 sp b554eda8 error 4 in libc-2.10.1.so[60c2000+13e000]

```Playing the file in VLC works fine, and identifies the audio stream as Vorb and the video stream as AVC1. This is on an Aspire One netbook. Any ideas are welcome.

---

