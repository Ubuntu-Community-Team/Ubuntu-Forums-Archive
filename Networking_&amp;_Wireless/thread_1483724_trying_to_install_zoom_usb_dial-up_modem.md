---
title: "trying to install zoom usb dial-up modem"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by bear672 on 2010-05-14
hello!
i'm trying to install zoom 3095 usb dial-up modem on my laptop which has ubuntu 9.10 on it but i got an error
 
[FONT=Times New Roman][SIZE=3]Where is the linux source build directory that matches your running kernel?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][lib/modules/2.6.31-21-generic/build][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Building modules for kernel 2.6.31-21-generic/build, using source directory[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]lib/modules/2.6.31-21-generic/build. Please wait...[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ERROR: Module build failed![/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Please examine the log file "/tmp/dgcconfig-buildlog.txt" to determine why.[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]dgcconfig-buildlog.txt said:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3](cd /lib/modules/2.6.31-21-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-21-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" clean)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.31-21-generic/build/.tmp_versions/dgcusbdcp.mod Modules.symvers GPL/hda/Modules.symvers[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3](cd /lib/modules/2.6.31-21-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.31-21-generic/build" "M=/usr/lib/dgcmodem/modules" "CC=gcc" modules)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make[1]: Entering directory `/usr/src/linux-headers-2.6.31-21-generic'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]scripts/Makefile.build:49: *** CFLAGS was changed in "/usr/lib/dgcmodem/modules/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make[1]: *** [_module_/usr/lib/dgcmodem/modules] Error 2[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-21-generic'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make: *** [all] Error 2[/SIZE][/FONT]
 
 
 
can anyone help me out?! i can't access internet on my laptop any other way right now. thanks~!

---

### Post by pdc on 2010-05-15
> i'm trying to install zoom 3095 usb dial-up modem on my laptop which has ubuntu 9.10 on it but i got an error

please explain which instructions you were following that lead you to doing all the stuff you were attempting to do:

in contrast, have a read at jkohler2's post: post #4 where he used gnome-ppp to configure: one would hope you would have similar joy in 9.10 

[http://ubuntuforums.org/showthread.php?t=1142241](http://ubuntuforums.org/showthread.php?t=1142241)

---

### Post by bear672 on 2010-05-15
well when i tried the gnome-ppp it said it couldn't find modem
so i used the zoom disc that came with the modem and followed the instructions for installing it on linux but that's what gave me the error. i tried looking on the website, linuxant, but i couldn't figure anything out.. and i don't undertstand that other thread that was posted.

---

### Post by pdc on 2010-05-15
in a terminal copy and paste the following

> dmesg | grep tty

and it will help us see what your system sees

---

### Post by bear672 on 2010-05-15
it said..
 
[FONT=Times New Roman][SIZE=3][    0.001681] console [tty0] enabled[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][   23.331112] cdc_acm 2-2:1.0: ttyACM0: USB ACM device[/SIZE][/FONT]

---

### Post by pdc on 2010-05-15
ttyACM0 means it is recognised as a modem;

what about: RIGHT-CLICK on network manager tab: most left of those at top right on top bar ..

click on Mobile broadband; Add: choose country then network if offered as option ....... select ........ if not google on apn settings for your provider ... all done? ........ close

now LEFT-CLICk on network manager ......... any joy?

I suspect when it said /dev/modem was not recognised you would have needed to look for and select ttyACM0 as the one to connect to ..

...... you could also try that if you wish before doing the above ..

---

