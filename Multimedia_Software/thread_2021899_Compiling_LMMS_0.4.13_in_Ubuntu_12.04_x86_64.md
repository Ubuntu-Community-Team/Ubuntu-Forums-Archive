---
title: "Compiling LMMS 0.4.13 in Ubuntu 12.04 x86_64"
date: 2012-07-10
forum: Multimedia Software
---

### Post by cre8ive65 on 2012-07-10
Hi
I am having issues compiling LMMS from source, I get stuck at the "make" command, at 87% it gives me this error

```
/usr/bin/ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/x86_64-linux-gnu/wine/libwinecrt0.a(exe_entry.o)) to format elf32-i386 (RemoteVstPlugin.c9kiSM.o) is not supported
winebuild: /usr/bin/ld failed with status 1
winegcc: winebuild failed
make[2]: *** [plugins/vst_base/RemoteVstPlugin] Error 2
make[1]: *** [plugins/vst_base/CMakeFiles/vstbase.dir/all] Error 2
make: *** [all] Error 2
```

Any ideas? :/

---

### Post by zizzdude on 2012-08-16
I, too, have the same issue here. Only thing I could think of is getting the 32 bit versions of wine-dev, but for some reason, it requires me to remove a good chunk of 64 bit packages I hope to keep.

---

### Post by SenChoi on 2012-08-24
I was having a same problem so i've been searching.

It seems this page has a solution.
[http://sourceforge.net/apps/phpbb/lmms/viewtopic.php?f=7&t=526](http://sourceforge.net/apps/phpbb/lmms/viewtopic.php?f=7&t=526)

But I can't understand.
orpheon7 says remove -m32 then it works fine.

Where is -m32?

---

