---
title: "compilation error"
date: 2009-12-29
forum: Multimedia Software
---

### Post by shariefbe on 2009-12-29
i am trying to compile one library called liboil. when i compile that i am getting this error. I goggled for this error its totally confusing for me. please help me.
```

Making all in uberopt
make[3]: Entering directory `/mnt/freescale/sources/liboil-0.3.16/examples/uberopt'
/bin/sh ../../libtool --tag=CC --mode=link arm-none-linux-gnueabi-gcc  -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops   -o uberopt  uberopt-uberopt.o ../../liboil/liboil-0.3.la -lm   
libtool: link: arm-none-linux-gnueabi-gcc -O3 -march=armv7-a -mtune=cortex-a8 -mcpu=cortex-a8 -mfloat-abi=softfp -mfpu=neon -ftree-vectorize -funroll-all-loops -o .libs/uberopt uberopt-uberopt.o  ../../liboil/.libs/liboil-0.3.so -lm -Wl,-rpath -Wl,/mnt/freescale//nfs-develop/usr/local/lib
uberopt-uberopt.o: In function `output_sequence':
uberopt.c:(.text+0x5c): undefined reference to `g_print'
uberopt.c:(.text+0xb4): undefined reference to `g_print'
uberopt.c:(.text+0x124): undefined reference to `g_print'
uberopt.c:(.text+0x168): undefined reference to `g_print'
uberopt.c:(.text+0x184): undefined reference to `g_print'
uberopt-uberopt.o:uberopt.c:(.text+0x1ac): more undefined references to `g_print' follow
uberopt-uberopt.o: In function `read_file':
uberopt.c:(.text+0x2d4): undefined reference to `g_file_get_contents'
uberopt.c:(.text+0x2f4): undefined reference to `g_strsplit'
uberopt-uberopt.o: In function `main':
uberopt.c:(.text+0x4f8): undefined reference to `g_print'
uberopt.c:(.text+0x520): undefined reference to `g_print'
uberopt.c:(.text+0x850): undefined reference to `g_print'
uberopt.c:(.text+0x888): undefined reference to `g_print'
uberopt.c:(.text+0x8a8): undefined reference to `g_print'
uberopt-uberopt.o:uberopt.c:(.text+0x8d4): more undefined references to `g_print' follow
uberopt-uberopt.o: In function `main':
uberopt.c:(.text+0x928): undefined reference to `g_random_int_range'
uberopt.c:(.text+0x94c): undefined reference to `g_random_int_range'
uberopt.c:(.text+0x970): undefined reference to `g_random_int_range'
uberopt.c:(.text+0x994): undefined reference to `g_random_int_range'
uberopt.c:(.text+0x9c8): undefined reference to `g_print'
uberopt.c:(.text+0xa08): undefined reference to `g_print'
uberopt.c:(.text+0xa80): undefined reference to `g_print'
uberopt.c:(.text+0xaac): undefined reference to `g_print'
collect2: ld returned 1 exit status
make[3]: *** [uberopt] Error 1
make[3]: Leaving directory `/mnt/freescale/sources/liboil-0.3.16/examples/uberopt'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/mnt/freescale/sources/liboil-0.3.16/examples'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/mnt/freescale/sources/liboil-0.3.16'
make: *** [all] Error 2
Building  of glib library  has failed 
sharief@sharief-desktop:/mnt/freescale/sources/liboil-0.3.16$ 

```

---

