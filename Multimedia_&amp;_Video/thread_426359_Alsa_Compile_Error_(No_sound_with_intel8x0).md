---
title: "Alsa Compile Error (No sound with intel8x0)"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by tical_84 on 2007-04-28
Hey Guys,
 Initially when i booted up with the live CD the sound worked great. After installing ubuntu I immediately had no sound.  I have been doing some research and I believe my ALSA drivers didn not install correctly. I found a little tutorial on howto troubleshoot some of my issues and i've followed it quite closely.  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I've tried doing this from the tutorial "Getting the ALSA drivers from a *fresh* kernel" (nothing happens still no sound) and i have tried " ALSA driver Compilation" in both when I am 


"Using drivers from alsa-project" and "Using alsa-source"
(where I have a compile error). I've tried using 'sudo module-assistant a-i alsa-source' and compiling manually.  For both instances this is I get the following error

 


In file included from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:726: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:745: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:1083: error: too many arguments to function ‘pci_save_state’
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:1087: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.12/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2

Can anybody shed some light here? :( 
Thanks.

---

### Post by tical_84 on 2007-04-28
bump....

---

### Post by nickthecook on 2008-02-13
I have the same issue with hda-intel:

make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.12  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.o
In file included from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:726: error: static declaration of ‘jiffies_to_msecs’ follows non-static declaration
include/linux/jiffies.h:264: error: previous declaration of ‘jiffies_to_msecs’ was here
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:745: error: static declaration of ‘msecs_to_jiffies’ follows non-static declaration
include/linux/jiffies.h:266: error: previous declaration of ‘msecs_to_jiffies’ was here
In file included from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:1083: error: too many arguments to function ‘pci_save_state’
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/alsa/alsa-driver-1.0.12/include/adriver.h:1087: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.12/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.12/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [compile] Error 2

---

### Post by nickthecook on 2008-02-13
Also, to add some details, my system was working fine, sound was great, until a system update. Then I started getting unknown symbol errors when loading module snd_hda_intel.

I was unable to resolve this, so I reinstalled ubuntu, and then installed all the packages I had installed before (generated a list of package before reinstall, and did "sudo apt-get install ..." for each of them).

Now I can load the snd_hda_intel module, but I'm seeing this in dmesg:

[   32.502447] hda_intel: azx_get_response timeout, switching to polling mode...

And as shown above, I can't compile the alsa driver myself.

Any help would be appreciated - my girlfriend can't watch movies on this thing now!

---

### Post by nickthecook on 2008-02-13
I got it to work by doing a "sudo apt-get install alsa-source", then untarring /usr/src/alsa-driver.tar.bz2 and making that instead of the one I had downloaded from the website.

I still don't have sound, and no errors in dmesg output, but I got the compile issue resolved.

---

