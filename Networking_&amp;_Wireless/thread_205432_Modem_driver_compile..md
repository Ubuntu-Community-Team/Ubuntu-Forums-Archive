---
title: "Modem driver compile."
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by chuckman78 on 2006-06-28
Hi all.

I am currently trying to install a winmodem in my ubuntu Dapper box. It uses an Intel 537EP chipset. I headed to the linmodems.org site (excellent site, great people) and after getting some data from my system, I got this response from Marvin, one of the site maintainers (I have introduced my comments and questions):

"Carlos,

Prepare for compiling by putting the Dapper CD in the drive, and then:

$ sudo apt-get install linux-headers-2.6.15-23-386 gcc-4.0 make

(**COMMENT: I believed that this is required to get the latest version of gcc, the compiler. Am I right? By the way I get an error response)

Then for your Intel537 modem, go to [http://developer.intel.com/design/mo...rt/drivers.htm](http://developer.intel.com/design/mo...rt/drivers.htm) through to [http://downloadfinder.intel.com/scri...9&submit=Go%21](http://downloadfinder.intel.com/scri...9&submit=Go%21)

Whereon you need the:
.
5) Modem Chipset Driver (Uncompiled) - [INTEL-537EP-2.60.80.0.TGZ] (1518KB)
2.60.80.0 8/9/2004 Download
Contains the base, partial open source, UNCOMPILED Intel(r) 537EP V.92 modem (PCI) chipset driver.

(**COMMENT: I got the file through the Windows boot and saved it in a FAT32 partition -/media/hda5 -in my box so I can see it with the ubuntu boot. I got another problem here. I made a new directory called /temporal and when I try to copy the intel*.tgz to it under GNOME I get permissions errors and can´t copy the file there. I had to go the terminal and use sudo cp. Is there a way to use GNOME to manage this?)

Under Linux:
$ tar zxf INTEL-537EP-2.60.80.0.TGZ

(**COMMENT: Had to use sudo tar .... I guess it is the permission stuff)

$ cd INTEL-537EP-2.60.80.0

(**COMMENT: I can´t get to that directory. I found that there was created a INTEL-537EP_secure-2.60.80.0 directory -beware of the secure in the middle of it- but I can´t cd to it. On GNOME I can´t open that folder either)

(**COMMENT: I can´t do anything from here on because of the previous problems)

Look around
$ ls
Clean up
$ make clean
Compile
$ make 537
and install
$ sudo make install

Hopefully, the modem will be found by:
$ sudo wvdialconf /etc/wvdial.conf
if the modem is found:
$ sudo gedit /etc/wvdial.conf
to a format like:

[Dialer Defaults]
Modem = /dev/modem
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = TargetPhoneNumber_without_spaces
Username = YourLoginName

Then try a dialout with:
$ sudo wvdial

MarvS
scanModem maintainer"

I hope that someone could help me with this problems. I had to install the winmodem because it looks like Dapper can´t work with my external US Robotics dialup modem. Thanks in advance for your time and help,

Regards,

Carlos.

---

### Post by zxee on 2006-06-29
> $ sudo apt-get install linux-headers-2.6.15-23-386 gcc-4.0 make

(**COMMENT: I believed that this is required to get the latest version of gcc, the compiler. Am I right? By the way I get an error response)
 
What error did you get?

> (**COMMENT: I got the file through the Windows boot and saved it in a FAT32 partition -/media/hda5 -in my box so I can see it with the ubuntu boot. I got another problem here. I made a new directory called /temporal and when I try to copy the intel*.tgz to it under GNOME I get permissions errors and can´t copy the file there. I had to go the terminal and use sudo cp. Is there a way to use GNOME to manage this?)

Under Linux:
$ tar zxf INTEL-537EP-2.60.80.0.TGZ

(**COMMENT: Had to use sudo tar .... I guess it is the permission stuff)


Most of the time it makes sense to put tar.gz files for compiling in your home directory.
Then you only use sudo for make install which is the linux way. 
You can install a script that lets you have root power in gnome; if that's what you want check out the features in automatix.

---

### Post by chuckman78 on 2006-06-29
[QUOTE=zxee]What error did you get? [/QUOTE]

I was getting an error related to "make" but I soved it, thanks anyway.

Right now I could make a little advance but now I am facing other problems. Next I will paste the terminal info that I get. I introduced son comments beginning with (*** because I had to translate that appear in my language, that is spanish.

carlos@mb-ubuntu:/temporal$ sudo make clean

cd coredrv; make clean
make[1]: se ingresa al directorio `/temporal/coredrv' (***make[1]: goes to folder `/temporal/coredrv' )
rm -f *.ko *.o *~ core
make[1]: se sale del directorio `/temporal/coredrv' (***make[1]: exits folder `/temporal/coredrv' )
rm -f *.o *.ko

carlos@mb-ubuntu:/temporal$ sudo make 537

Module precompile check
Current running kernel is: 2.6.15-23-386
/lib/modules... autoconf.h exists
diff: /boot/vmlinuz.autoconf.h: No existe el fichero o directorio (***file or folder doesn´t exists)
autoconf.h matches running kernel
diff: /boot/vmlinuz.version.h: No existe el fichero o directorio (***file or folder doesn´t exists)
version.h matches running kernel
2.6.15-23-386
make[1]: se ingresa al directorio `/temporal/coredrv' (***make[1]: goes to folder `/temporal/coredrv' )
make -C /lib/modules/2.6.15-23-386/build SUBDIRS=/temporal/coredrv modules
/usr/src/linux-headers-2.6.15-23-386/scripts/gcc-version.sh: line 11: gcc: orden no encontrada (*** instruction not found)
/usr/src/linux-headers-2.6.15-23-386/scripts/gcc-version.sh: line 12: gcc: orden no encontrada (*** instruction not found)
make[2]: gcc: No se encontro el programa (***program not found)
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.15-23-386' (goes to folder `/usr/src/linux-headers-2.6.15-23-386')
CC [M] /temporal/coredrv/coredrv.o
/bin/sh: gcc: orden no encontrada (***instruction not found)
make[3]: *** [/temporal/coredrv/coredrv.o] Error 127
make[2]: *** [_module_/temporal/coredrv] Error 2
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.15-23-386' (exits folder `/usr/src/linux-headers-2.6.15-23-386')
make[1]: *** [537core_26] Error 2
make[1]: se sale del directorio `/temporal/coredrv' (***make[1]: exits folder `/temporal/coredrv' )
2.6.15-23-386
Failed to build driver

What could be wrong? Thanks in advance for your help.

Regards,

Carlos.

---

### Post by nrayever on 2006-06-30
hi carlos:

i'm having the same problem with that modem. i can't still believe that there's no support for this modem's in ubuntu. even if this modem is "100% compatible" with linux, ubuntu developers may have forgot about this modem. let's face it....  to have linux is better to have a broadband connection. i hope somebody makes a nice script to install it or something like that, would be helpful.

sincerly nrayever

---

### Post by Matchless on 2006-06-30
Carlos,
        Could you try it with the process in the wiki dialupmodemhowto for the Intel536ep, using the file you downloaded for 537. I have never tried the 537 but someone mentioned somewhere that the same process for the 536 should work. My experience is that you should clean out all the files created during a failed install for Intel537 before trying again from scratch. Also only use the extracted file once where possible. If you use a nice file manager (I use krusader) then it becomes easy to finsd all the files by using search etc.
Hope this helps

---

### Post by chuckman78 on 2006-07-01
Hi, all.

Matchless, I have been succesfull with the installation of the 537EP under Dapper. I made it in part using the Wiki Howto Dialup modem and the information I got from this thread:

[http://www.ubuntu-es.org/comment/reply/5503/40456](http://www.ubuntu-es.org/comment/reply/5503/40456)

I tried on Breazy and Dapper and worked in both of them. I will as soon as I can (I am on my weekend work shift) try to put all the steps together (the link is in spanish, and I had to use steps from the wiki and the link) and have them on the net. 

I would like to thank all of you guys for your invaluable help, you people rock!

Regards,

Carlos.

---

### Post by Matchless on 2006-07-01
Carlos,
         I am glad you got it working! Yes, it would be nice if you could post an Howto for the modem in English

---

### Post by chuckman78 on 2006-07-06
Hi, guys.

I have compiled a little Howto about all this 537EP stuff. you can find it here:

<[http://ubuntuforums.org/showthread.php?t=209840]("http://ubuntuforums.org/showthread.php?t=209840")>

Regards,

Carlos.

---

