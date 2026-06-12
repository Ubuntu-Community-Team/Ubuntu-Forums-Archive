---
title: "Problems with &quot;Comprehensive Sound Problem Solutions Guide v0.5e&quot;"
date: 2009-03-29
forum: Multimedia Software
---

### Post by dspisak on 2009-03-29
I had good sound  until recently.  Then it just disappeared.  I've tried the various methods in "Comprehensive Sound Problem Solutions Guide v0.5e" several times without any success.  I get many error messages.  Here they are.

When I tried: &#8220;Using alsa-source&#8221;
I get this error message: &#8220;Build of the package alsa-source failed!&#8221; (at 50%)
/usr/src/modules/alsa-driver/acore/sound.c:100: warning: format not a string literal and no format arguments
CC [M]  /usr/src/modules/alsa-driver/acore/init.o
/usr/src/modules/alsa-driver/acore/init.c: In function &#8216;snd_card_register&#8217;:                                                       
/usr/src/modules/alsa-driver/acore/init.c:568: warning: passing argument
5 of &#8216;device_create&#8217; makes pointer from integer without a cast
/usr/src/modules/alsa-driver/acore/init.c:568: warning: format not a string literal and no format arguments
CC [M]  /usr/src/modules/alsa-driver/acore/memory.o
CC [M]  /usr/src/modules/alsa-driver/acore/info.o
/usr/src/modules/alsa-driver/acore/info.c: In function &#8216;resize_info_buffer&#8217;:                                                      
/usr/src/modules/alsa-driver/acore/info.c:90: error: implicit  &#9474; declaration of function &#8216;PAGE_ALIGN&#8217;                                       
make[5]: *** [/usr/src/modules/alsa-driver/acore/info.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic&#8217;
make[2]: *** [compile] Error 2
make[2]: Leaving directory `/usr/src/modules/alsa-driver'
make[1]: *** [build-stamp] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [kdist_image] Error 2


When I try: &#8220;Using drivers from alsa-project - update&#8221;
After&#8221;sudo make&#8221; I get these errors:
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:39:3: error: #error Invalid value of HZ.
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:247:31: error: division by zero in #if
In file included from memalloc.inc:13,
                 from memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: At top level:
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:718: error: static declaration of &#8216;jiffies_to_msecs&#8217; follows non-static declaration
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:286: error: previous declaration of &#8216;jiffies_to_msecs&#8217; was here
In file included from memalloc.inc:13,
                 from memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:721:31: error: division by zero in #if
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: In function &#8216;jiffies_to_msecs&#8217;:
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:726: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: At top level:
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:737: error: static declaration of &#8216;msecs_to_jiffies&#8217; follows non-static declaration
/usr/src/linux-headers-2.6.27-11-generic/include/linux/jiffies.h:288: error: previous declaration of &#8216;msecs_to_jiffies&#8217; was here
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:742:31: error: division by zero in #if
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h: In function &#8216;msecs_to_jiffies&#8217;:
/usr/src/alsa/alsa-driver-1.0.12rc2/include/adriver.h:747: error: &#8216;CONFIG_HZ&#8217; undeclared (first use in this function)
memalloc.c: In function &#8216;snd_malloc_pages&#8217;:
memalloc.c:268: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
memalloc.c:268: warning: passing argument 1 of &#8216;mark_pages&#8217; makes pointer from integer without a cast
memalloc.c: In function &#8216;snd_free_pages&#8217;:
memalloc.c:289: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
memalloc.c:289: warning: passing argument 1 of &#8216;unmark_pages&#8217; makes pointer from integer without a cast
memalloc.c: In function &#8216;snd_malloc_dev_pages&#8217;:
memalloc.c:315: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
memalloc.c:315: warning: passing argument 1 of &#8216;mark_pages&#8217; makes pointer from integer without a cast
memalloc.c: In function &#8216;snd_free_dev_pages&#8217;:
memalloc.c:332: error: &#8216;CONFIG_PAGE_OFFSETUL&#8217; undeclared (first use in this function)
memalloc.c:332: warning: passing argument 1 of &#8216;unmark_pages&#8217; makes pointer from integer without a cast
make[1]: *** [memalloc.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.12rc2/acore'
make: *** [compile] Error 1


After &#8220;sudo make install&#8221; I get these errors
rm -f /lib/modules/0.0.0/misc/snd*.*o /lib/modules/0.0.0/misc/persist.o /lib/modules/0.0.0/misc/isapnp.o
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.12rc2/acore'
mkdir -p /lib/modules/0.0.0/misc
cp snd-page-alloc.o snd-pcm.o snd-timer.o snd.o /lib/modules/0.0.0/misc
cp: cannot stat `snd-page-alloc.o': No such file or directory
cp: cannot stat `snd-pcm.o': No such file or directory
cp: cannot stat `snd-timer.o': No such file or directory
cp: cannot stat `snd.o': No such file or directory
make[1]: *** [_modinst__] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.12rc2/acore'
make: *** [install-modules] Error 1


Now what do I do?  TIA.

Here is my system:
MB - Asus M3A78-T
CPU - AMD Phenom II x4 810 3.18 GHz
Memory - Crucial PC8500 2GB
On-board video - ATI HD 3300
On-board audio - ATI Technologies Inc SBx00 Azalia (Intel HDA)
 (or ATI Technologies Inc RS780 Azalia controller, lspci -v returns both audio devices)  I think the driver is hda-intel.

4/6/09 edit: The problem is solved.  I followed soundcheck's instructions on the "ALSA Upgrade Script" thread and re-installed ALSA.  I did not have to re-install either ubuntu or the kernel.  The video was not affected.

Dan

---

