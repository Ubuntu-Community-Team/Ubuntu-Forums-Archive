---
title: "Can't get SPDIF Working!"
date: 2009-10-30
forum: Multimedia Software
---

### Post by Zaptor on 2009-10-30
I'm on Jaunty with an ASUS Nvidia ION M/B and I can't get S/PDIF working, only HDMI.

Here is what i tried:

Change hdmi in
      
     ```
/etc/asound.conf 
 
```to
     
     ```
pcm.!default {

   type plug
   slave {
       pcm "iec958"
   }

} 
```But when i do a 

     ```
speaker-test -c 2 
``` i get an error saying no such file or folder.

Also the S/PDIF output does not emit any light, seems switched off somehow so i did a aplay -l and got this (sorry for the Swedish)
```

     
     xbmc@htpc:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: NVidia [HDA NVidia], enhet 0: VT1708S Analog [VT1708S Analog]
  Underordnade enheter: 2/2
  Underordnad enhet nr. 0: subdevice #0
  Underordnad enhet nr. 1: subdevice #1
kort 0: NVidia [HDA NVidia], enhet 3: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0 
```S/PDIF seem to be gone!? How can i get it back?

---

### Post by Zaptor on 2009-10-30
Problem solved, uppgrade to Alsa .21 and unmute the previously hidden IEC958.

How to uppgrade:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wget build-essential linux-headers-`uname -r`
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2)
tar -xf alsa-driver-1.0.21.tar.bz2
cd alsa-driver-1.0.21
./configure
make
sudo make install
sudo ./snddevices
sudo apt-get install alsa-utils
#Reboot Here!!!
alsamixer
sudo alsactl store

---

### Post by b4uno8 on 2009-10-31
Thanks very much, Zaptor!

This worked just fine for me.  I have an Asus AT3N7A-I with
Ubuntu 9.04  :D

---

### Post by Zaptor on 2009-10-31
> **b4uno8 said:**
> Thanks very much, Zaptor!

This worked just fine for me.  I have an Asus AT3N7A-I with
Ubuntu 9.04  :D

Good on you! :)

Running the exact same setup as you, just curious... have you found a replacement fan for the CPU? the stock 6000rpm fan is driving me nuts!

---

### Post by b4uno8 on 2009-11-02
Hey Zaptor,

Thanks again for the help with SPDIF.

I am using the original fan that came with the mbo.
It is a bit noisy.  I read recently that ASUS switched
to 4100 RPM fans from 6400 RPM fans.  I guess that I
have the 4100 one.  I cannot tell from looking at it
whether it is 4100 or 6400.  I guess that is just a
standard 40 mm fan that you can replace for 300 yen.
I saw something on this recently.  Here is the 
link: [http://www.legitreviews.com/article/1079/1/](http://www.legitreviews.com/article/1079/1/)

---

