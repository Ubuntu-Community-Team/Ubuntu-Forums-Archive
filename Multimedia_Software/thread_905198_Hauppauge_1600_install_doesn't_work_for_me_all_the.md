---
title: "Hauppauge_1600 install doesn't work for me all the sudden"
date: 2008-08-30
forum: Multimedia Software
---

### Post by pcozzy on 2008-08-30
I installed ultimate 1.9
normally I find no problems with other older installs of ultimate except this one.

I follow this guide:
[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600")

now when I sudo make in v4l..
I get this error:

```
~/v4l-dvb$ sudo make
make -C /home/pctech/v4l-dvb/v4l 
make[1]: Entering directory `/home/pctech/v4l-dvb/v4l'
creating symbolic links...
Kernel build directory is /lib/modules/2.6.24-21-generic/build
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/pctech/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/pctech/v4l-dvb/v4l/cpia.o
/home/pctech/v4l-dvb/v4l/cpia.c: In function 'cpia_open':
/home/pctech/v4l-dvb/v4l/cpia.c:3205: error: implicit declaration of function 'current_uid'
make[3]: *** [/home/pctech/v4l-dvb/v4l/cpia.o] Error 1
make[2]: *** [_module_/home/pctech/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/pctech/v4l-dvb/v4l'
make: *** [all] Error 2
```

I tried to research with google and I don't even know what to look for.
I am thinking the kernel build that I have has something different.
is there a sudo make menuconfig in ubuntu thats what I used in gentoo?
not that this is the right direction to take.
any help will be greatly appreciated.

---

### Post by Skerit on 2008-08-30
I'm experiencing the same problem with Manu Abraham's latest multiproto ...

---

### Post by pcozzy on 2008-08-30
I didn't do anything special since my first post as far as correcting this problem.

All I did was rm -f v4l-dvb then started all over with the process and at the section where i run :  hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

And it worked for me compiling v4linux.

The only thing I can think of is that I was trying download source at 4:00am eastern time when it didn't work compared to 4:00pm eastern time.  So I guess be patient and try again.
thanx.

---

