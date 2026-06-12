---
title: "something wrong about ospfd"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by chuyinsu on 2009-03-05
I downloaded the source code here:
www dot ospf dot org-->Release 2.0-->gzipped tar format

and there're errors when I run "make install".

I noticed that I might have to install some packages first:
gcc
g++
glibc
glibc-devel
libstdc++-devel
make
Tcl

some of above I managed to install(like gcc) but some I cannot find via "apt-get". e.g. I cannot find glibc and glibc-devel and libstdc++-devel using "sudo apt-get install (package name)" or "sudo aptitude install (package name)". So do some packages have other names in Ubuntu?

and when I unzipped the package:
sudo tar xvzf ***.tar.gz
and went into the directory
cd ospfd/linux
then:
make install
it failed.
I figured that this is an formal&fixed release so there shouldn't be something wrong in the source code. Maybe I made some mistakes without realizing them.

I'd be very appriciated if someone can told how to install this...

P.S. error messages:

cys@cys-laptop:~/temp/ospfd/linux$ sudo make install

g++ -MD -O -g -Wall -Woverloaded-virtual -Wcast-qual -Wuninitialized -I. -I../src -I/usr/local/include -c linux.C
In file included from ../src/ospfinc.h:24,
                 from linux.C:33:
./machdep.h:93: [error]&#65306; C [function]&#8216;char* strptime(char*, const char*, const tm*)&#8217;[declaration]
/usr/include/time.h:210: [error]&#65306; conflict with the previous declaration &#8216;char* strptime(const char*, const char*, tm*)&#8217;
make: *** [linux.o] [error] 1
cys@cys-laptop:~/temp/ospfd/linux$ 

the words with [] like [error], [function] are in Chinese originally and I translated them into English.
I tried to change the function in machdep.h, which is 
char* strptime(char*, const char*, const tm*)
into:
char* strptime(const char*, const char*, tm*)
and there is another error:
../src/dbage.C:117: [error]&#65306; &#8216;GetNextAdj&#8217;[is not declared in dbage.C]

very confused.
I'm using Ubuntu 8.10
thanks!

---

### Post by puppywhacker on 2009-03-05
In ubuntu the developers packages are named -dev and not -devel.
So for instance "glibc-dev" 
These contain the header files needed to compile programs that use those packages.

Your error is in
/usr/include/time.h

which is part of a package named something like linux-kernel-headers-dev. I bet that this package is already installed.

I think ospfd was written for a different kernel version than what you have now. Compiling breaks because the definition GCC is confused about the redefinition of the method "strptime" 

(I don't have an Ubuntu machine here to verify the correct names)

---

### Post by chuyinsu on 2009-03-06
Thanks for your reply.

Maybe I have to change the Linux kernel to an old one...-_-;;;
I'll try that in a couple of days.

---

### Post by handfoot4work on 2010-11-10
> **chuyinsu said:**
> Thanks for your reply.

Maybe I have to change the Linux kernel to an old one...-_-;;;
I'll try that in a couple of days.

hi,All

I'm read your post the ospfd installation on you post  [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1087480](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1087480) , now can you  install it yet?.

I have problem to install ospfd source code too. Could you please! suggest me the step too?

---

