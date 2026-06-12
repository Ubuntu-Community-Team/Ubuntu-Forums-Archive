---
title: "Creative soundcard has anyone installed one ?"
date: 2012-01-03
forum: Multimedia Software
---

### Post by Bakedasin on 2012-01-03
First of all a big hi to all of you at ubuntu bells,sirens,fireworks and whistles going off,No seriously you do a fantastic job of guiding mere mortals around the system and I thank you all for it as I have benefited on many occasions.
The card in question is an creative audigi XFi [model no= sb0460,I have downloaded creatives efforts in the form of a tar.gz file. I have been following the compiling easy how to guide and have got the files into the /usr/local/src folder and taken charge of that folder permissions wise.I have then tried a sudo make and this is the output I got

ewen@ewen-desktop:~$ cd'/usr/local/src' 
bash: cd/usr/local/src: No such file or directory
ewen@ewen-desktop:~$ cd /usr/local/src
ewen@ewen-desktop:/usr/local/src$ autogen.sh
autogen.sh: command not found
ewen@ewen-desktop:/usr/local/src$ sudo make
[sudo] password for ewen: 
make -C /lib/modules/2.6.32-37-generic/build M=/usr/local/src
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-37-generic'
  LD      /usr/local/src/built-in.o
  CC [M]  /usr/local/src/xfi.o
/usr/local/src/xfi.c:14:26: error: sound/driver.h: No such file or directory
/usr/local/src/xfi.c: In function ‘ct_card_probe’:
/usr/local/src/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/usr/local/src/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/usr/local/src/xfi.o] Error 1
make[1]: *** [_module_/usr/local/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-37-generic'
make: *** [all] Error 2
ewen@ewen-desktop:/usr/local/src$ 

The other thing is i'm trying to do this on 10.4 LTS

Here are the contents of /usr/local/src 
/usr/local/src/built-in.o
/usr/local/src/COPYING
/usr/local/src/ct20k1reg.h
/usr/local/src/ct20k2reg.h
/usr/local/src/ctamixer.c
/usr/local/src/ctamixer.h
/usr/local/src/ctatc.c
/usr/local/src/ctatc.h
/usr/local/src/ctdaio.c
/usr/local/src/ctdaio.h
/usr/local/src/ctdrv.h
/usr/local/src/cthardware.c
/usr/local/src/cthardware.h
/usr/local/src/cthw20k1.c
/usr/local/src/cthw20k2.c
/usr/local/src/ctimap.c
/usr/local/src/ctimap.h
/usr/local/src/ctmixer.c
/usr/local/src/ctmixer.h
/usr/local/src/ctpcm.c
/usr/local/src/ctpcm.h
/usr/local/src/ctresource.c
/usr/local/src/ctresource.h
/usr/local/src/ctsrc.c
/usr/local/src/ctsrc.h
/usr/local/src/ctutils.h
/usr/local/src/ctvmem.c
/usr/local/src/ctvmem.h
/usr/local/src/Disk.id
/usr/local/src/Makefile
/usr/local/src/README
/usr/local/src/xfi.c

I don't know what the first file is as it wasn't in the original untarred file
I'm not that good with computers so please bear with me we all start somewhere me many years ago
If anyone can advance upon my efforts I will be astounded but I probably shouldn't be because you guys make it look like falling off a log
A BIG thanks in advance if any one can help with this as to me its looking unlikely.
Thanks

---

