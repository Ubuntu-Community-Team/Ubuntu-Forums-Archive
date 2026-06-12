---
title: "[SOLVED] which bit-version of firefox?"
date: 2008-02-13
forum: Mythbuntu
---

### Post by tomashektor on 2008-02-13
Not sure if this post belong in the mythbuntu forum or the x86 64bit, but anyway...I have the amd64 version of mythbuntu installed. I've been trying to resolve the flash player problem in firefox. Two questions: if I have the amd64 os, does this also mean that firefox is a 64-bit version or could it be a 32-bit? And how can I look this up?

---

### Post by kidders on 2008-02-14
Hi there,

You can have either ... or both.

The best way to spot the difference between a 64-bit app and a 32-bit one is to examine an executable binary or library belonging to it...```
$ file /path/to/realplay.bin 
realplay.bin: **ELF 32-bit** LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped
$ file /path/to/firefox-bin
firefox-bin: **ELF 64-bit** LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.9, dynamically linked (uses shared libs), stripped
```

---

### Post by tomashektor on 2008-02-14
Thanks! Will try that when I come home.

---

