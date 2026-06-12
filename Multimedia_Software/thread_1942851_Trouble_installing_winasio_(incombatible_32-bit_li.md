---
title: "Trouble installing winasio (incombatible 32-bit libraries?)"
date: 2012-03-18
forum: Multimedia Software
---

### Post by megamasha on 2012-03-18
```

rob@SCKubuntu:~/temp/wineasio$ make
winegcc -shared -m32 wineasio.dll.spec -mnocygwin -L/usr/lib32/wine -L/usr/lib32 -o wineasio.dll.so asio.o main.o regsvr.o     -ljack  -lodbc32 -lole32 -lwinmm -luuid
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.5.4/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.5.4/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status
winegcc: gcc-4.5 failed
make: *** [wineasio.dll.so] Error 2
rob@SCKubuntu:~/temp/wineasio$
```I get the above output when trying to install wineasio on an amd64 system running kubuntu 11.10. I have copied asio.h into the folder (are there 32/64-bit versions of this file?), and I believe I have the latest versions of all required packages. I realise something somewhere must falsely be the 32 version..., or I have a wrongly-set 32 bit flag somewhere in the makefile perhaps?

Perhaps I should be using /usr/lib**32**/gcc/x86_64-linux-gnu/4.5.4/libgcc.a?

I just don't know how to go about fixing this. Can anyone help?

MM

---

### Post by cyberfooks on 2012-03-20
Hi,

I'm pretty sure that you are missing the 4.5.x Multilib. ;-)

Try:

apt-get install g++-4.5-multilib

---

### Post by megamasha on 2012-03-20
That'd be the one :-)
 Is there a complete list of required ubuntu packages anywhere?

---

### Post by NodeEndo on 2012-12-20
:KS
For anyone still having trouble installing and configuring WineASIO 0.9.0 with Wine 1.5 on Ubuntu 12.10 (amd64), I've started a dedicated blog on blogger.com to host a complete tutorial that I've written on how to accomplish this. 
*Tell me what you think, feedback on my blog will be very much appreciated.
-Enjoy!
[http://linuxmusiciansunite.blogspot.com/](http://linuxmusiciansunite.blogspot.com/)

---

