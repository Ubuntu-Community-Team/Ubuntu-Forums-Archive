---
title: "Replay Gain (no mp3gain package) in 18.04"
date: 2018-05-09
forum: Multimedia Software
---

### Post by kazakore on 2018-05-09
How can you add Replay Gain to an mp3 in Ubuntu 18.04?

mp3gain has been the most regularly recommended way, this was removed in 16.04 although there was a GUI version called easymp3gain which apparently worked but I used the .deb from 14.04 and that worked fine from the terminal like I want.

mp3gain from 14.04 doesn't work now, it installs fine but I get this output:
```
 mp3gain x.mp3 
==13923== AddressSanitizer CHECK failed: ../../../../src/libsanitizer/asan/asan_rtl.cc:411 "((!asan_init_is_running && "ASan init calls itself!")) != (0)" (0x0, 0x0)
    #0 0x7f88530240cd (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x120cd)
    #1 0x7f885302aeb3 (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x18eb3)
    #2 0x7f8853025088 (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x13088)
    #3 0x7f885301afb9 (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x8fb9)
    #4 0x7f88530271f2 (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x151f2)
    #5 0x7f8855fb8aa7 (/lib/x86_64-linux-gnu/ld-2.27.so+0x17aa7)
    #6 0x7f8855fac3eb (/lib/x86_64-linux-gnu/ld-2.27.so+0xb3eb)
    #7 0x7f88529e9da5 (/lib/x86_64-linux-gnu/libc-2.27.so+0x166da5)
    #8 0x7f88524610e3 (/lib/x86_64-linux-gnu/libdl-2.27.so+0x10e3)
    #9 0x7f88529ea2de (/lib/x86_64-linux-gnu/libc-2.27.so+0x1672de)
    #10 0x7f88529ea36e (/lib/x86_64-linux-gnu/libc-2.27.so+0x16736e)
    #11 0x7f8852461734 (/lib/x86_64-linux-gnu/libdl-2.27.so+0x1734)
    #12 0x7f8852461165 (/lib/x86_64-linux-gnu/libdl-2.27.so+0x1165)
    #13 0x7f885302fb3b (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x1db3b)
    #14 0x7f8853022ff3 (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x10ff3)
    #15 0x7f8853024a3a (/usr/lib/x86_64-linux-gnu/libasan.so.0.0.0+0x12a3a)
    #16 0x7f8855fb1805 (/lib/x86_64-linux-gnu/ld-2.27.so+0x10805)
    #17 0x7f8855fa20c9 (/lib/x86_64-linux-gnu/ld-2.27.so+0x10c9)

```

I looked at trying the easymp3gain package from 16.04 but it has listed in it's depends the unavailable mp3gain package....


How can I set Replay Gain to my mp3s? Preferably CLI. Why has mp3gain even gone?

---

### Post by kazakore on 2018-05-09
Seems there's the source of a first new version for a long time on sourceforge but my compiling fails.

```
@/mp3gain-1_6_1-src$ make
cc -Wall -DHAVE_MEMCPY   -c -o mp3gain.o mp3gain.c
mp3gain.c:97:10: fatal error: mpg123.h: No such file or directory
 #include <mpg123.h>
          ^~~~~~~~~~
compilation terminated.
<builtin>: recipe for target 'mp3gain.o' failed
make: *** [mp3gain.o] Error 1

$ sudo apt-get install mpg123
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mpg123 is already the newest version (1.25.10-1).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by kazakore on 2018-05-09
I'm not going to mark as solved just now but this package from Debian seems to be working correctly....

[https://packages.debian.org/wheezy/amd64/mp3gain/download](https://packages.debian.org/wheezy/amd64/mp3gain/download)

---

### Post by ajgreeny on 2018-05-09
You may be better off using bthe PPA repository at [https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio?field.series_filter=bionic](https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio?field.series_filter=bionic)

All the needed info on adding the repo is shown on the link.

---

### Post by kazakore on 2018-05-10
> **ajgreeny said:**
> You may be better off using bthe PPA repository at [https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio?field.series_filter=bionic](https://launchpad.net/~flexiondotorg/+archive/ubuntu/audio?field.series_filter=bionic)

All the needed info on adding the repo is shown on the link.

Ahh thanks, I would have done but I've just found out by pretty much random what has replaced it. This appears to be the most recent implementation of Replay Gain and similar EBU technologies. I downloaded it before checking and it's also in the official repos. Shame nobody managed to tell me that when 16.04 was released and seems still not many people know now....

[https://sourceforge.net/projects/bs1770gain/files/bs1770gain/](https://sourceforge.net/projects/bs1770gain/files/bs1770gain/)


So
# apt-get install bs1770gain
then either set up an alias (although the options format is completely different) or use the new command seems to be the best way to do this currently. :)


EDIT: Except it doesn't seem to support the option to write to encoded data like mp3gain does, hence support is limited, especially on portable music players etc, so it really doesn't fulfil all my requirements and think I'm back to using the old (removed) mp3gain so thanks again for the ppa link....

---

### Post by Yellow Pasque on 2018-05-10
For future reference, when you're missing a header (.h) file, you need the appropriate -dev package.
```
fatal error: mpg123.h: No such file or directory
```
means you needed libmpg123-dev

---

### Post by kazakore on 2018-05-11
> **Temüjin said:**
> For future reference, when you're missing a header (.h) file, you need the appropriate -dev package.
```
fatal error: mpg123.h: No such file or directory
```
means you needed libmpg123-dev

Ahhh thanks. I confirmed I had the library but not the development files. That makes sense to me and I'll remember to check -dev files as well in future :)

---

