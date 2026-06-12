---
title: "Lubuntu audio problems with Flash Player"
date: 2015-06-05
forum: Multimedia Software
---

### Post by Dertuny on 2015-06-05
Hello!! 
I want to install Lubuntu 14.04 at LG S1 Express dual notebook with Intel HDA / Realtek ac880:
lspci: 00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02).
Is strange because youtube and system apparently sounds good and clear, but in a specific pages with Flash videos, the sound becomes noise, it's horrible!!
I tryed to add a line: options snd-hda-intel model=MODEL (Lg, auto, ...)in 
 /etc/modprobe.d/alsa-base.conf

But no changes, nothing new happens, the problem not solved.
I found a Realtek audio driver in [http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/) (HD audio codecs), version 3.0 Linux, but I can't compile, the errors when i make:

make[1]: se ingresa al directorio «/usr/src/linux-headers-3.16.0-38-generic»
  CC [M]  /home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/hwdep.o
  CC [M]  /home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/memory_wrapper.o
  CC [M]  /home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/memalloc.o
  CC [M]  /home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/sgbuf.o
  CC [M]  /home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm.o
  CC [M]  /home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.o
/home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c: In function ‘snd_pcm_file_fd’:
/home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:1647:2:
 error: implicit declaration of function ‘fget_light’ 
[-Werror=implicit-function-declaration]
  file = fget_light(fd, fput_needed);
  ^
/home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:1647:7:
 warning: assignment makes pointer from integer without a cast [enabled 
by default]
  file = fget_light(fd, fput_needed);
       ^
/home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c: In function ‘snd_pcm_lib_mmap_iomem’:
/home/linux/Descargas/Rt-Linux-HDaudio-5.18/alsa-driver-RTv5.18/alsa/acore/pcm_native.c:3453:26:
 warning: unused variable ‘runtime’ [-Wunused-variable]
  struct snd_pcm_runtime *runtime = substream->runtime;;

I tried the same Lubuntu on a desktop computer, and another notebooks and the sound is perfect at the same web pages.

This is my first message here (sorry, my english is not very good) and my last attempt to solve this problem, if not solved here I let the idea of installing Lubuntu at notebook (or any Linux, I tried another distros and the same problem appeared)....

Thanks!!!

---

### Post by Rob Sayer on 2015-06-05
I wouldn't be too quick to install drivers from the maker's page.  It looks good on paper but those things are not always properly maintained.  Search first for other cases of your problem first.  Always.

Have you installed lubuntu-resticted-extras?

---

### Post by Dertuny on 2015-06-05
I tried all i found on www, forums, packages, included restricted extras...nothing solved the problem. 
I tried with the same live usb with persistence and sound runs very good at all except Lg (only my lg have intel hda realtek sound i think)....

---

### Post by Dertuny on 2015-06-13
I tried other distros and all have the same problem. I tried lubuntu 14.04 32 bit with flash-nonfree-extrasound and the problem not solved. I tried installig the last kernel and older kernels and nothing new happened. Finally, i tried ubuntu 12.04.5 and realtek drivers downloaded from realtek web page, the drivers works good but the problem with flash not solved.
I don't know what happens with that notebook / sound card / graphics card (ati mobility x1600)...this problem is driving me crazy!!! Help, please!!!
Add: Now, youtube in fullscreen sounds bad too...

---

### Post by Rob Sayer on 2015-06-15
Seems to be an old computer with support issues.  Have you seen this?

[http://askubuntu.com/questions/461391/how-to-make-audio-work-on-old-laptop](http://askubuntu.com/questions/461391/how-to-make-audio-work-on-old-laptop)

---

### Post by Dertuny on 2015-06-18
Yes, is an old computer....but, i have another more old computer and this problems not appears. Well, thanks for reply. I tried all i see at page and nothing changed. 
Youtube in flash mode, for example, when i set full screen, the sound becomes a little bit slow and with clicks, I tried with html5 and the sound is perfect, with fullscreen too.

---

### Post by Dertuny on 2015-06-21
I found something...I tryed to boot lubuntu with "nomodeset" option and the problem was solved. But, the screen resolution is bad, i need a 1280x800 and is not possible to set that in this mode. Well, I think the problem is not flash or audio drivers, is just the old graphics card with no support and is impossible to install drivers from ATI website, only is possible to use Open Source drivers. With nomodeset, glxgears shows 700 Fps, and in "normal" mode, only 60 Fps.
I'm searching things about config the opensource drivers, or similar, but i don't have lucky. 
What i can do knowing this now?? Any ideas?? 
Thanks!!

---

### Post by Dertuny on 2015-06-25
I uninstalled "xserver-xorg-video-ati" package, and all the problems are solved. Now youtube runs good and the other webs with flash videos too. I still having 3d acceleration and the system uses radeon driver (strange):
lspci -v
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc.  [AMD/ATI] RV530/M56-P [Mobility Radeon X1600] (prog-if 00 [VGA  controller])
	Kernel driver in use: radeon
Thanks.
Problem solved!!!!

---

