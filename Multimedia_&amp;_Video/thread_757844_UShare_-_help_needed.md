---
title: "UShare - help needed"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by mvavrik on 2008-04-17
So, I have installed Ubuntu 8.04 and am attempting to install **UShare** in order to stream movies to my Xbox 360. I'm new so bear with me and please let me know if I fail to include any relevant information.

I will be attentive of my post and will try to respond to your responses immediately because I know there will be questions.


**I have UShare and have attempted to configure it, receiving this output:**

user@Ubuntu:/root/ushare-1.1$ sudo ./configure
Checking for compiler available...
gcc is unable to create an executable file.
If gcc is a cross-compiler, use the --cross-compile option.
C compiler test failed.
See file "config.log" produced by configure for more details.
user@Ubuntu:/root/ushare-1.1$ 

**I have downloaded the latest release of GCC and attempted to configure that:**

user@Ubuntu:~/Desktop/gcc-4.3.0$ sudo ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

**Some relevant information from "config.log" seems to be the following:**

Thread model: posix
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
configure:3166: $? = 0
configure:3168: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:3171: $? = 1
configure:3194: checking for C compiler default output file name
configure:3197: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status



I have gone through the forums and read the other posts on UShare but haven't been able to get it working.  If motivation is needed....I dumped the idea of using Vista to stream movies and instead installed Ubuntu.

---

### Post by mssever on 2008-04-18
Have you installed build-essential?

---

### Post by mvavrik on 2008-04-18
I was able to solve the problem by reinstalling the GCC 4.2.0 (loaded with fresh Unbuntu install) using the Package Manager. Thanks

---

