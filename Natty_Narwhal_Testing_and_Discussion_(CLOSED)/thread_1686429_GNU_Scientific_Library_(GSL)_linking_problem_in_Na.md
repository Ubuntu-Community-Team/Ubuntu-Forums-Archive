---
title: "GNU Scientific Library (GSL) linking problem in Natty"
date: 2011-02-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by WebDrake on 2011-02-12
I'm having problems linking to the GSL in Natty.  libgsl0-dev and libgsl0ldbl have been installed via aptitude, but attempting to link to them creates an error:

```
g++ -ansi -pedantic -Wall -O2 -march=native -mtune=native -I. -lm -lgsl -lgslcblas test.cpp -o test
/tmp/cczTqRyQ.o: In function `main':
test.cpp:(.text+0x191): undefined reference to `gsl_rng_mt19937'
test.cpp:(.text+0x196): undefined reference to `gsl_rng_alloc'
test.cpp:(.text+0x221): undefined reference to `gsl_rng_set'
test.cpp:(.text+0x3b6): undefined reference to `gsl_ran_flat'
test.cpp:(.text+0x3fd): undefined reference to `gsl_ran_flat'
test.cpp:(.text+0x57e): undefined reference to `gsl_ran_flat'
test.cpp:(.text+0x10e5): undefined reference to `gsl_rng_free'

```

The same code builds in Maverick with no problem.  Checking what libraries are installed reveals,

```
~$ ldconfig -p | grep gsl
        libgslcblas.so.0 (libc6,x86-64) => /usr/lib/libgslcblas.so.0
        libgslcblas.so.0 (libc6) => /usr/lib32/libgslcblas.so.0
        libgslcblas.so (libc6,x86-64) => /usr/lib/libgslcblas.so
        libgslcblas.so (libc6) => /usr/lib32/libgslcblas.so
        libgsl.so.0 (libc6,x86-64) => /usr/lib/libgsl.so.0
        libgsl.so.0 (libc6) => /usr/lib32/libgsl.so.0
        libgsl.so (libc6,x86-64) => /usr/lib/libgsl.so
        libgsl.so (libc6) => /usr/lib32/libgsl.so
```

Any suggestions what might be wrong?  It's difficult to imagine this is a bug in GSL per se, but perhaps in its packaging, or g++ in Natty?

I'm running the amd64 version of Natty alpha.

Thanks in advance for any suggestions.

---

### Post by WebDrake on 2011-02-12
Appears to relate to order of arguments provided to g++.

```
g++ -ansi -pedantic -Wall -O2 -march=native -mtune=native -I. -lm -lgsl -lgslcblas test.cpp
```fails, but

```
g++ -ansi -pedantic -Wall -O2 -march=native -mtune=native -I. test.cpp -lm -lgsl -lgslcblas
``` builds just fine.

What's changed in Natty to mean the first of these no longer works?

---

### Post by mc4man on 2011-02-12
It's come up a couple of times here, probably just changes in 4.5.X
It's likely more proper to put the source before deps/links/pc anyway.
recent ex. [here ]("http://ubuntuforums.org/showthread.php?t=1669713")(orig had .c at end

Also noticed some odd linking issues w/ some sources that built fine in 10.10 though haven't ck.'ed recently - [noted here]("http://ubuntuforums.org/showthread.php?t=1646152")

And again haven't ck.'ed recently ( will shortly). but some sources will not compile correctly as static w/ gcc-4.5 (notably ffmpeg

---

### Post by MadCow108 on 2011-02-12
the change is probably related to the addition of --as-needed to the default flags of gcc which produces a lot of linking problems
using --no-as-needed makes it work

```
g++ -Wl,--no-as-needed -ansi -pedantic -Wall -O2 -march=native -mtune=native -I. -lm -lgsl -lgslcblas test.cpp -o test
```

---

