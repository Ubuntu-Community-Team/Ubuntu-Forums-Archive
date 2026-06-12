---
title: "can't install sound drivers please help"
date: 2009-03-29
forum: Multimedia Software
---

### Post by sthprkfnt on 2009-03-29
This is only my first day using ubuntu and I have no sound I am running an alieware m17x laptop i've downloaded the linux drivers for my sound card but as a noob I have no idea how to install them can someone help translate the readme into terms I can understand.

Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure
	c. make
	d. make install
	e. alsaconf
	f. ./snddevices (Only kernel 2.4 does it)

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note: 	1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
	2. Kernel Version must be 2.2.14 or later.
	3. All mixer channels are muted by default. You must use a native
		or OSS mixer program to unmute appropriate channels.
	4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
	5. The driver added to support the SPDIF functoin. 	
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org](www.alsa-project.org), then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package.

---

### Post by sthprkfnt on 2009-03-29
bump

---

### Post by sthprkfnt on 2009-03-29
if someone could i.m. me and walk me through this I would appreciate it [email]supersthprkfnt@hotmail.com[/email]

---

### Post by SHENGTON on 2009-03-29
Hello sthprkfnt, good evening. :)

I think you shouldn't need to install drivers for your audio card. They should work out of the box in ubuntu. You probably just need to adjust the mixer settings.

Take care and God bless. :)

---

### Post by sthprkfnt on 2009-03-29
I've turned the volume on everything in the mixer all the way up but there is no sound btw i'm running 9.04

---

### Post by khelben1979 on 2009-03-29
[Alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") is a good program for sound mixing.

And if it isn't installed:
```
sudo apt-get install alsamixer
```

---

### Post by sthprkfnt on 2009-03-29
THANK YOU THANK YOU THANK YOU khelben1979 ALSA mixer fixed it *hugs* much much love thanks again

---

### Post by khelben1979 on 2009-03-29
That's good news! Always nice to hear when my efforts does matter. :)

---

