---
title: "need help compiling pchdtv 5500 drivers in edgy"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by ronacc on 2006-10-28
I am trying to compile the pchdtv drivers in 6.10 (release) and getting nowhere.
I have installed the kernal source and build essentials here is the output when I try to run make


  code:
ron@ron-desktop:~/Temp/v4l-dvb/v4l$ make
scripts/make_makefile.pl
creating symbolic links...
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/ron/Temp/v4l-dvb/v4l  modules
make[1]: Entering directory `/lib/modules/2.6.17-10-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.17-10-generic/build'
make: *** [default] Error 2
ron@ron-desktop:~/Temp/v4l-dvb/v4l$ 


seeing that the kernal source and header dirs were in /usr/src/  and not in /lib/modules/2.6.17-10-generic/build I tried symlinking them to /lib/modules/2.6.17-10-generic/build
I have also tried sudo make and also from an "SU" terminal same exact output each time.
I have read the threads on pchdtv and tried what was sugested that seemed remotely appropriate all with no luck.
any help on what I'm missing would be appreciated.:-?

---

### Post by oblib on 2006-10-28
Try doing a 'make distclean' or just 'make clean' and then 'make' and see if that fixes it.

---

### Post by ronacc on 2006-10-28
that didn't work neither did deleting the whole dir and starting fresh from the tar.gz off of the pchdtv or from a fresh download of the tar.gz from the pchdtv site . it always stops at the "modules" point and there are so many "nested" make files I havent been able to track that down yet. running make with the -p switch looks like everything should go alright but it dosent.

---

### Post by ronacc on 2006-10-28
Well I just wiped the hd and did a fresh install . the bkn symlinks are still there so appearantly they are broken "out of the box" , havent tried the drivers yet I have to d/l the kernal source and build essentials , and I seem to have lost my customizations and addons for nothing.

---

### Post by ralyon on 2006-11-06
I was able to get my pcHDTV 5500 working with the new drivers from v4l-dvb website. I'll try and list the steps I took from memory so let me know if you find any errors with it. I am using the 2.6.17-10-generic kernel on an amd64 cpu, fyi.

Pre: Set up the build environment.

1. Go to [http://linuxtv.org/hg/v4l-dvb?cmd=tags;style=gitweb](http://linuxtv.org/hg/v4l-dvb?cmd=tags;style=gitweb) and click on "tree" to the right of "tip"

2. Click on "gz" or "bz2" near the top to download the drivers.

3. Extract the drivers then copy the folder to /usr/src. (Rename the folder if you like. I will use v4l-dvb in my code examples)

4. Open terminal and
```
cd /usr/src/v4l-dvb
make allyesconfig
sed -i s/"CONFIG_SOUND_ACI_MIXER=m"/"CONFIG_SOUND_ACI_MIXER=n"/1 v4l/.*config
sed -i s/"CONFIG_SOUND_ACI_MIXER := m"/"CONFIG_SOUND_ACI_MIXER := n"/1 v4l/.*config
make
sudo make install
```

5. Reboot the machine.

It should load the drivers automatically on boot, if not try a 
```
sudo modprobe -rv cx88-blackbird cx88-dvb
sudo modprobe -v cx88-dvb
```

If that works you should blacklist the blackbird driver.

Good Luck. :D

---

### Post by ronacc on 2006-11-07
thanks for the tip I followed your instructions and the drivers built and installed ok. I tried getatsc -dvb 0 14 | mplayer -  and nothing was piped to mplayer . so I tried  ron@ron-desktop:~$ sudo modprobe -rv cx88-blackbird cx88-dvb   and sudo modprobe -v cx88-dvb and got this error
note I am not using the default kernal I had installed 2.6.18 hoping that the drivers would be in there as promised by pchdtv (they wernt). should I revert to 2.6.17 ?


rmmod /lib/modules/2.6.18/kernel/drivers/media/common/ir-common.ko
rmmod /lib/modules/2.6.18/kernel/drivers/i2c/algos/i2c-algo-bit.ko
rmmod /lib/modules/2.6.18/kernel/drivers/media/video/video-buf.ko
rmmod /lib/modules/2.6.18/kernel/drivers/media/video/tveeprom.ko
rmmod /lib/modules/2.6.18/kernel/drivers/media/video/btcx-risc.ko
ron@ron-desktop:~$ sudo modprobe -v cx88-dvb
insmod /lib/modules/2.6.18/kernel/drivers/media/video/video-buf.ko 
insmod /lib/modules/2.6.18/kernel/drivers/media/dvb/dvb-core/dvb-core.ko 
WARNING: Error inserting dvb_core (/lib/modules/2.6.18/kernel/drivers/media/dvb/dvb-core/dvb-core.ko): Invalid module format
insmod /lib/modules/2.6.18/kernel/drivers/media/video/video-buf-dvb.ko 
WARNING: Error inserting video_buf_dvb (/lib/modules/2.6.18/kernel/drivers/media/video/video-buf-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
insmod /lib/modules/2.6.18/kernel/drivers/media/dvb/frontends/dvb-pll.ko 
insmod /lib/modules/2.6.18/kernel/drivers/media/video/btcx-risc.ko 
insmod /lib/modules/2.6.18/kernel/drivers/media/video/v4l2-common.ko 
WARNING: Error inserting v4l2_common (/lib/modules/2.6.18/kernel/drivers/media/video/v4l2-common.ko): Invalid module format
insmod /lib/modules/2.6.18/kernel/drivers/media/video/v4l1-compat.ko 
WARNING: Error inserting v4l1_compat (/lib/modules/2.6.18/kernel/drivers/media/video/v4l1-compat.ko): Invalid module format
insmod /lib/modules/2.6.18/kernel/drivers/media/video/videodev.ko 
WARNING: Error inserting videodev (/lib/modules/2.6.18/kernel/drivers/media/video/videodev.ko): Invalid module format
insmod /lib/modules/2.6.18/kernel/drivers/media/video/tveeprom.ko 
insmod /lib/modules/2.6.18/kernel/drivers/i2c/algos/i2c-algo-bit.ko 
insmod /lib/modules/2.6.18/kernel/drivers/media/common/ir-common.ko 
insmod /lib/modules/2.6.18/kernel/drivers/media/video/cx88/cx88xx.ko 
WARNING: Error inserting cx88xx (/lib/modules/2.6.18/kernel/drivers/media/video/cx88/cx88xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
insmod /lib/modules/2.6.18/kernel/drivers/media/video/cx88/cx8802.ko 
WARNING: Error inserting cx8802 (/lib/modules/2.6.18/kernel/drivers/media/video/cx88/cx8802.ko): Unknown symbol in module, or unknown parameter (see dmesg)
insmod /lib/modules/2.6.18/kernel/drivers/media/video/cx88/cx88-vp3054-i2c.ko 
insmod /lib/modules/2.6.18/kernel/drivers/media/video/cx88/cx88-dvb.ko 
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.18/kernel/drivers/media/video/cx88/cx88-dvb.ko): Unknown symbol in module, or unknown parameter (see dmesg)
ron@ron-desktop:~$

---

### Post by ralyon on 2006-11-08
That was for 2.6.17. When I tried 2.6.18 mine came up with no extra steps (although it didn't fix my other problem.) I think you have a conflict with your drivers from that message. Whats you dmesg say? 'dmesg | grep cx88'

---

### Post by ronacc on 2006-11-08
I had compiled and installed 2.6.18 before I built v4l and had built against 2.6.18 v4l seemd to build with the 2.6.18 headers etc ( hard to tell the ubuntu build sys isnt very informative and I couldnt find where to make  it more verbose) and they were instaled in the proper dir (2.6.18).
dmesg said about the same as the above post, no additional clues.and none of the video modules loaded on reboot. I nuked  the 2.6.18 install and reverted to 2.6.17 generic and I'll try from there.
where do I set bash to give verbose output and more history ? I looked in ~.bash.rc but didn't see anything there where is the global bash.rc ?

---

