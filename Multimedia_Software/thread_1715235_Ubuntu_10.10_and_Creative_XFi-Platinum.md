---
title: "Ubuntu 10.10 and Creative XFi-Platinum"
date: 2011-03-26
forum: Multimedia Software
---

### Post by Alqamar on 2011-03-26
Hello there. I finally decided to install Ubuntu 10.10, and have been it Ubuntu for a week. Things look fine; I specially like the way Ubuntu lets me twist my keyboard setup (I need to be able to type things such as &#7811; and ÿ with a Spanish keyboard, and now I can...) 

I'm also able to hear music with my Logitech Clearchat Headphones.

But I would like to get sound from my Creative Soundblaster X-Fi Platinum. It works fine with Windows XP SP3.

1º problem: I click on Sound Preferences > Hardware > SB X-Fi and...

I have got a 2.1 Creative Speakers System. It's not in the list, so I have to choose another one.

2º problem: No sound comes from the speakers, no matter which speakers option I choose.

I tried to install the XFI Linux drivers from Creative's website, following the instructions from here:
[http://opensource.creative.com/soundcard.html](http://opensource.creative.com/soundcard.html)

but the installation failed. This is what I got.

myname@myname-desktop:~/Descargas$ ls
XFiDrv_Linux_Public_US_1.00  XFiDrv_Linux_Public_US_1.00.tar.gz
myname@myname-desktop:~/Descargas$ cd XFiDrv_Linux_Public_US_1.00
myname@myname-desktop:~/Descargas/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.35-28-generic/build M=/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  LD      /home/myname/Descargas/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/myname/Descargas/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00/xfi.c:14: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2
myname@myname-desktop:~/Descargas/XFiDrv_Linux_Public_US_1.00$ make install
Copy module files...
mkdir: cannot create directory `/lib/modules/2.6.35-28-generic/kernel/drivers/ssound': Permission denied
make: *** [install] Error 1
myname@myname-desktop:~/Descargas/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for myname: 
make -C /lib/modules/2.6.35-28-generic/build M=/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/myname/Descargas/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00/xfi.c:14: fatal error: sound/driver.h: No such file or directory
compilation terminated.
make[2]: *** [/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/myname/Descargas/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [all] Error 2
myname@myname-desktop:~/Descargas/XFiDrv_Linux_Public_US_1.00$ sudo make installCopy module files...
cp: cannot stat `ctxfi.ko': No such file or directory
make: *** [install] Error 1
myname@myname-desktop:~/Descargas/XFiDrv_Linux_Public_US_1.00$ sudo make uninstall
Remove module files...
Update module dependency relationships...
myname@myname-desktop:~/Descargas/XFiDrv_Linux_Public_US_1.00$

---

### Post by Alqamar on 2011-03-27
I have tried to follow this guide:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

But... as far as I know, everything looks ok... and there is not any sound.

---

### Post by Alqamar on 2011-04-03
I installed some additional packages (from the Ubuntu Software Center) for the PulseAudio Server, and now my speakers are working perfectly. The soundcard disappeared when I selected Digital Output, and I have to use a 4.1 configuration because the one I have (2.1) isn't in the list.

It's now working, but I would like to know what I did, just in order to learn a bit more...

---

### Post by Alqamar on 2011-04-07
It stopped working again. The speakers are giving me some headaches in Windows too, so I'm unplugging them and checking them with a different computer.

---

