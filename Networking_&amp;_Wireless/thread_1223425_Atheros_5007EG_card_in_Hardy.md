---
title: "Atheros 5007EG card in Hardy"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by aj_the_first on 2009-07-26
I am really getting to the point that I think tarballs are a great conspiracy by the linux-nerds out there just to make fools out of all the average linux users

Okay, I just tried (and failed) to install yet another tarball.  None have ever worked properly.
This was me trying to get my atheros 5007eg wireless card to work.  I have found tons of threads on this card not working with Hardy,and they all mention that hardy does not properly identify the card, which is the case for me.  My lspci lists the card as:   Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
Which is how all the threads state the card is misidentified
Now, I tried any fixes I could find in the threads, and none of them work... at least not for me for some reason.  Some guy even called everyone liars that said that his fix did not work...

So I decided I would try to madwifi.
I downloaded the madwifi tarball, compiled it, and then "make"... here is what happened:
aj@Linus:~/Desktop/madwifi-0.9.4$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-24-generic/build SUBDIRS=/home/aj/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-generic'
  CC [M]  /home/aj/Desktop/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/aj/Desktop/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/aj/Desktop/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/aj/Desktop/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:27:19: error: errno.h: No such file or directory
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:29:20: error: string.h: No such file or directory
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'uudecode_usage':
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: At top level:
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:40: error: expected ')' before '*' token
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:70: error: expected ')' before '*' token
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c: In function 'main':
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'FILE' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: (Each undeclared identifier is reported only once
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: for each function it appears in.)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:121: error: 'src_stream' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'dst_stream' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:122: error: 'NULL' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:130: warning: implicit declaration of function 'getopt'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:134: error: 'optarg' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: implicit declaration of function 'exit'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:138: warning: incompatible implicit declaration of built-in function 'exit'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:141: error: 'optind' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:142: error: 'stdin' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:144: warning: implicit declaration of function 'fopen'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: implicit declaration of function 'fprintf'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:146: error: 'stderr' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: implicit declaration of function 'strerror'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: error: 'errno' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:147: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:148: warning: incompatible implicit declaration of built-in function 'exit'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:152: warning: incompatible implicit declaration of built-in function 'exit'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: implicit declaration of function 'get_line_from_file'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:156: warning: assignment makes pointer from integer without a cast
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:157: warning: implicit declaration of function 'strncmp'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:164: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:165: warning: incompatible implicit declaration of built-in function 'exit'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:168: warning: implicit declaration of function 'strtoul'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: implicit declaration of function 'strchr'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:170: warning: incompatible implicit declaration of built-in function 'strchr'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:172: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:173: warning: incompatible implicit declaration of built-in function 'exit'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:178: warning: implicit declaration of function 'strcmp'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:179: error: 'stdout' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_WRONLY' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_CREAT' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:182: error: 'O_TRUNC' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:186: error: 'O_EXCL' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:188: warning: implicit declaration of function 'open'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXU' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXG' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:189: error: 'S_IRWXO' undeclared (first use in this function)
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:191: warning: implicit declaration of function 'fdopen'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:193: warning: incompatible implicit declaration of built-in function 'fprintf'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:194: warning: format '%s' expects type 'char *', but argument 4 has type 'int'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:195: warning: incompatible implicit declaration of built-in function 'exit'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:199: warning: implicit declaration of function 'read_stduu'
/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode.c:201: warning: implicit declaration of function 'fclose'
make[3]: *** [/home/aj/Desktop/madwifi-0.9.4/ath_hal/uudecode] Error 1
make[2]: *** [/home/aj/Desktop/madwifi-0.9.4/ath_hal] Error 2
make[1]: *** [_module_/home/aj/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-24-generic'
make: *** [modules] Error 2


so...  does anyone have any idea why I can't install this driver or how else to get my card working?

I've got many many many other problems with Hardy that I am have ing a serious headache with as well, but I'll post other threads.
I just backdated from Jaunty becasue I have one of the unsupported ATI x1200 chips, and have constant screen flicker issues and no 3D accelleration with the open source driver, BUT, in Jaunty I was able to fix all my problems, I even fixed the screen flicker, AND it had few problems to fix in the first place.
Now I want to go back to Jaunty and put up with no 3D game-playing just because of how difficult EVERYTHING is proving to be in Hardy...
Grr...

Thanks in advance for any help that may come.
AJ

---

