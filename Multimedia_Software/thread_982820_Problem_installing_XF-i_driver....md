---
title: "Problem installing XF-i driver..."
date: 2008-11-15
forum: Multimedia Software
---

### Post by Martin B on 2008-11-15
Hello,

The other day I downloaded the new "XFiDrv_Linux_Public_US_1.00" Linux driver from Creative's site. My OS is Mythbuntu 8.04, my card is XF-i Xtreme Music

I followed the instructions in the Readme file and first ran "make", then "make install", both with Sudo.
Below is the result from my "make" attempt. I did not get any farther than this...

martin@Martin-Ubuntu:~/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.24-21-generic/build M=/home/martin/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/martin/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
martin@Martin-Ubuntu:~/XFiDrv_Linux_Public_US_1.00$ 
martin@Martin-Ubuntu:~/XFiDrv_Linux_Public_US_1.00$ 

Can somebody please tell me what the warnings are about and what I am doing wrong, this is driving me nuts! Have been waiting for a driver for more than a year and when it finally comes along it cannot be installed...

BR
Martin

---

### Post by notedopjes on 2008-12-13
Hi,

I initially got the same problem, but after recompiling my kernel i was able to succesfully complie the x-fi driver.

I have a 2.6.25-gentoo-r7 kernel. 

Correct settings:
Sound card support should be build as module as is:
= ALSA (Advanced linux soundcard architecture)
== Sequencer support

At first i hadn't Sequencer support included and got the same problems you had. 

However after succesfully compiled the X-FI driver and after a: 

modprobe -a ctxfi

No soundcards where found when trying:

cat /proc/asound/cards

Anyone have a clue on how to proceed from here?

Regards,

Marc

---

