---
title: "Trying to compile driver for DVICO DVB-T Dual"
date: 2006-06-08
forum: Multimedia &amp; Video
---

### Post by Frank-Hamersley on 2006-06-08
Hello all - please forgive my obvious ignorance...

Notwithstanding problems with the ATI driver, I am trying to compile Chris Pascoe's DVICO v4.1 driver for a DVB-T Dual card.  However I am not very familiar with building "stuff" on Ubuntu and seem to be missing some packages...what they are, I have no idea, but seems to be something to do with modules!

Can anyone provide some tips on what I need to do next?

Cheers, Frank.
------------------------------------------------------------------
root@hp5150dvt:/usr/src/v41-dvb/v4l-dvb-2f259866534d# make
make -C /usr/src/v41-dvb/v4l-dvb-2f259866534d/v4l
make[1]: Entering directory `/usr/src/v41-dvb/v4l-dvb-2f259866534d/v4l'
creating symbolic links...
make -C /lib/modules/2.6.15-23-amd64-generic/build SUBDIRS=/usr/src/v41-dvb/v4l-dvb-2f259866534d/v4l  modules
make[2]: Entering directory `/lib/modules/2.6.15-23-amd64-generic/build'
make[2]: *** No rule to make target `modules'.  Stop.
make[2]: Leaving directory `/lib/modules/2.6.15-23-amd64-generic/build'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/v41-dvb/v4l-dvb-2f259866534d/v4l'
make: *** [all] Error 2
root@hp5150dvt:/usr/src/v41-dvb/v4l-dvb-2f259866534d#
------------------------------------------------------------------

---

### Post by fabertawe on 2006-07-10
I'm trying to build the plustek_pp scanner module as my scanner doesn't work 'out of the box' as it apparently should (ditto my printer but that's another hair-puller).

Anyway, I was getting the same error as you - "*** No rule to make target `modules'. Stop." but got past it with this...

```
sudo apt-get install build-essential linux-headers-2.6.15-25-amd64-k8
```

But now I'm stuck here...

```
Check for root - done.

Check for kernelversion:
Using makefile for kernel 2.6.x
Build-directory:
/usr/share/doc/libsane/plustek/build
Removing build-directory - done.
Creating build-directory - done.

Linking source files...ls: /usr/share/doc/libsane/plustek/../../backend/plustek-pp_*.c: No such file or directory
ls: /usr/share/doc/libsane/plustek/../../backend/plustek-pp_*.h: No such file or directory
 - done.
Copying Makefile to build-directory - done.
Making the module...
make: Entering directory `/usr/src/linux-headers-2.6.15-25-amd64-k8'
make[1]: *** No rule to make target `/usr/share/doc/libsane/plustek/build/plustek-pp_dac.o', needed by `/usr/share/doc/libsane/plustek/build/pt_drv.o'.  Stop.
make: *** [_module_/usr/share/doc/libsane/plustek/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.15-25-amd64-k8'
There were some build errors...

```

I've searched many, many, many threads (and Googled extensively) and not found anything helpful.

Paul

---

### Post by Frank-Hamersley on 2006-07-10
G'day fab,

Have had to put this aside for a bit...but FWIR I had to add the "universe" and I think "restricted" in /etc/apt/sources.list.

Don't forget (as I did) to run "apt-get update" immediately afterwards to freshen the database _before_ doing any "apt-get installs".

Cheers, Frank.

---

### Post by fabertawe on 2006-07-11
> **Frank-Hamersley said:**
> G'day fab,

Have had to put this aside for a bit...but FWIR I had to add the "universe" and I think "restricted" in /etc/apt/sources.list.

Don't forget (as I did) to run "apt-get update" immediately afterwards to freshen the database _before_ doing any "apt-get installs".

Cheers, Frank.

Hi Frank,

I've already done all this, thanks. I'm two weeks into Linux and have been enjoying it but trying to get my scanner to work is **really** frustrating me ](*,) 

Cheers anyway!

Paul

---

