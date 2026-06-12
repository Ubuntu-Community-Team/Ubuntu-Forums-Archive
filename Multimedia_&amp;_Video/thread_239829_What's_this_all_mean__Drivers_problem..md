---
title: "What's this all mean?  Drivers problem."
date: 2006-08-19
forum: Multimedia &amp; Video
---

### Post by saxofoner on 2006-08-19
I'm trying to install my drivers, and this as far as I got...
```
julian@saxofone:~/Desktop/alsa-driver-1.0.4$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/julian/Desktop/alsa-driver-1.0.4
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
julian@saxofone:~/Desktop/alsa-driver-1.0.4$ make
find: /usr/src/linux-2.4.18-3: No such file or directory
find: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4: No such file or directory
find: /usr/src/linux-2.4.18-3: No such file or directory
find: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4: No such file or directory
find: /usr/src/linux-2.4.18-3: No such file or directory
find: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4: No such file or directory
make dep
find: /usr/src/linux-2.4.18-3: No such file or directory
find: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4: No such file or directory
find: /usr/src/linux-2.4.18-3: No such file or directory
find: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4: No such file or directory
find: /usr/src/linux-2.4.18-3: No such file or directory
find: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4: No such file or directory
make[1]: Entering directory `/home/julian/Desktop/alsa-driver-1.0.4'
make[2]: Entering directory `/home/julian/Desktop/alsa-driver-1.0.4/acore'
Makefile:5: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4/toplevel.config: No such file or directory
Makefile:6: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4/Makefile.conf: No such file or directory
Makefile:11: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4/alsa-kernel/core/Makefile: No such file or directory
Makefile:15: /usr/src/linux-2.4.18-3/alsa-driver-1.0.4/Rules.make: No such file or directory
make[2]: *** No rule to make target `/usr/src/linux-2.4.18-3/alsa-driver-1.0.4/Rules.make'.  Stop.
make[2]: Leaving directory `/home/julian/Desktop/alsa-driver-1.0.4/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/julian/Desktop/alsa-driver-1.0.4'
make: *** [include/sndversions.h] Error 2
julian@saxofone:~/Desktop/alsa-driver-1.0.4$


```

---

### Post by saxofoner on 2006-08-19
Sorry maybe I should have been more descriptive.  It's an a8n5x, and I need my sound to work ... Is there an easier way?  I don't knowwhat alsa is.

---

### Post by gherardo on 2006-08-20
Try reading ouput ;) 

These are the last lines put out by 'configure', followed by your 'make':

[INDENT]checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
**Please, install the package with full kernel sources** for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
julian@saxofone:~/Desktop/alsa-driver-1.0.4$ make[/INDENT]

configure stopped because it missed something (full kernel sources) and explicitly asked you to install it. There's no point in make-ing after incomplete configuration.
version 
Try to install kernel-headers for your kernel (issue 'uname -r' to find this out) with synaptic, then redo configure and, IF SUCCESSFUL, do make.

Gherardo

---

### Post by tseliot on 2006-08-20
Try this:
```
sudo apt-get install linux-headers-`uname -r`
```

(use this ` and not ' !)

then:
```
./configure --with-kernel=/usr/src/linux-headers-`uname -r`
```

---

### Post by saxofoner on 2006-08-20
Okay, I thought I was missing that, but I didn't know what it was, so I was clueless...

---

### Post by saxofoner on 2006-08-20
I did sudo apt-get install linux-headers-2.6.15-26-386 and then I did the second thing and got errors.  Here's the last few lines of them...

```
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:358:1: warning: multi-line comment
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:377:1: warning: multi-line comment
  LD [M]  /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../acore/seq/oss/snd-seq-oss.o
  CC [M]  /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/dummy.o
In file included from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/../alsa-kernel/drivers/dummy.c:27,
                 from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/dummy.c:1:
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:358:1: warning: multi-line comment
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:377:1: warning: multi-line comment
  CC [M]  /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/mtpav.o
In file included from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/../alsa-kernel/drivers/mtpav.c:58,
                 from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/mtpav.c:1:
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:358:1: warning: multi-line comment
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:377:1: warning: multi-line comment
  CC [M]  /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serial-u16550.o
In file included from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/../alsa-kernel/drivers/serial-u16550.c:38,
                 from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serial-u16550.c:1:
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:358:1: warning: multi-line comment
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:377:1: warning: multi-line comment
In file included from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serial-u16550.c:1:
/home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/../alsa-kernel/drivers/serial-u16550.c:676:5: warning: "SNDRV_SERIAL_MS124W_MB_NOCOMBO" is not defined
  CC [M]  /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serialmidi.o
In file included from /home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serialmidi.c:31:
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:358:1: warning: multi-line comment
/home/julian/Desktop/alsa-driver-1.0.4/include/sound/core.h:377:1: warning: multi-line comment
/home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serialmidi.c: In function ‘tx_loop’:
/home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serialmidi.c:325: warning: passing argument 3 of ‘driver->write’ makes integer from pointer without a cast
/home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serialmidi.c:325: error: too many arguments to function ‘driver->write’
make[3]: *** [/home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers/serialmidi.o] Error 1
make[2]: *** [/home/julian/Desktop/alsa-driver-1.0.4/kbuild/../drivers] Error 2
make[1]: *** [_module_/home/julian/Desktop/alsa-driver-1.0.4/kbuild] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-386'
make: *** [compile] Error 2
```

---

### Post by gherardo on 2006-08-20
Looks like mismatched kernel-version. Did you really issue the apt-get as Tseliot said? kernel-headers' version must match _running_ kernel version _exactly _.

Gherardo

---

### Post by gherardo on 2006-08-20
Oooops... maybe it's simpler. Did you clean out the building dir?
Try

```
make clean
```

before configuring. Usually there's a "clean" rule in the Makefile. Just give it a try.

G.

---

### Post by saxofoner on 2006-08-20
Thanks, I'll try that when I get home.

---

### Post by saxofoner on 2006-08-21
....stpr...mumblemumble....  *mumbles*

I tried it all over again, with the make clean, and it gave me a similar/same error message.  More "multiline comment" errors, and that ERROR 2 thing.

---

