---
title: "Audio Driver not loaded properly??"
date: 2010-01-14
forum: Mythbuntu
---

### Post by Peter Martin on 2010-01-14
Audio card Creative Alchemy an X-Fi type.

Last winter I managed to get Mythbuntu 8.10 up with all working except audio. My audio board then was an Auzen X-Fi Prelude 7.1 unit. The card produced great audio but had no Linux driver. It uses a Creative X-Fi chip. The creative Linux driver activated part of the PCB but not enough to be useful.

This winter I've had time to try again. I bought/installed the Creative audio card noted above. When I started Mythbuntu 8.10 the sound worked fine. -  The program notified me that my software was out of date, so I let it install 9.04, all went well. So I told the software update manager to load 9.10. Some distance into the load, it stopped in Terminal mode. Since I didn't know what to do, I made a live 9.10 CD and did a new install. This deleted the audio driver. I have tried to reinstall the audio driver.

When I go to settings to setup audio, it recognizes the new card, but with everything turned up I still have know audio.

The process I used to install the driver:-
- Ran tar -zxvf XFiDrv_Linux_Public_US_1.00.tar.gz
- Cd'd to the new directory made by the tar command.
- ran 'make'
- sudo make install

The 'make install' stopped on error.
"cp; cannot stat 'ctxfi.ko'; no such file or Dir"
"make; *** [install] error 1"

This driver worked on 8.10, so I've done something wrong?
Do I somehow clean thing up and start over, or is the process wrong??

Some words of wisdom will be much appreciated.

Peter

---

### Post by azmyth on 2010-01-14
I'm surprised make didn't give you an error.

$make clean

look in the directory for an install readme. Also, look for a config file that you may've needed to run first.

If no, run make again and look to see if there's an error you missed which is usually a missing header file in a dependency that's not installed.

---

### Post by Peter Martin on 2010-01-16
You're right! Thanks, 'Make' did produce errors.
I wondered if some where along the line I had buggered things up, so I noted the errors and then reinstalled mythbuntu 9.10. 
The 'make' command produces the same errors now. Here they are:
- - - - - - - - - 
peter@Peter-HDTV:~/Downloads/XFiDrv_Linux_Public_US_1.00$ ls
COPYING      ctatc.c   cthardware.c  ctimap.h   ctresource.c  ctvmem.c  xfi.c
ct20k1reg.h  ctatc.h   cthardware.h  ctmixer.c  ctresource.h  ctvmem.h
ct20k2reg.h  ctdaio.c  cthw20k1.c    ctmixer.h  ctsrc.c       Disk.id
ctamixer.c   ctdaio.h  cthw20k2.c    ctpcm.c    ctsrc.h       Makefile
ctamixer.h   ctdrv.h   ctimap.c      ctpcm.h    ctutils.h     README
peter@Peter-HDTV:~/Downloads/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.31-17-generic/build M=/home/peter/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  LD      /home/peter/Downloads/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/peter/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/peter/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: **error: sound/driver.h: No such file or directory**
/home/peter/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/peter/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: **error: implicit declaration of function ‘snd_card_new’**
/home/peter/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/peter/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/peter/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [all] Error 2
- - - - - - - - - 
Should I be doing this from a system dir instead of a user dir?
Maybe I'm not run 'make' as root?

I had this driver installed and working on mythbuntu 8.10

here is pertinent part of README
- - - - - -
In terminal,

1) Goto source directory
2) Execute make command as root
   make
   make install
- - - - - - - 

Any more suggestions???

Peter

---

