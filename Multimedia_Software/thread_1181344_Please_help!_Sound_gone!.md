---
title: "Please help! Sound gone!"
date: 2009-06-07
forum: Multimedia Software
---

### Post by Sashin on 2009-06-07
After installing some codecs from realtek, my sound has disappeared and I have no idea how to uninstall them.

[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PFid=24&Level=4&Conn=3&DownTypeID=3)

If I had done it by deb file I could do it, but it was some install script...

---

### Post by Sashin on 2009-06-07
UPDATE: I've tried reinstalling, pulse, alsa and ubuntu-desktop, none of it worked.

---

### Post by techclown on 2009-06-07
Have you tried to right click on the volume in the tray to see if it is muted?

---

### Post by Sashin on 2009-06-07
Of course! 
I'm pretty sure the problem has to do with the thing I installed, but I'm not sure how to uninstall it.
I installed it from a script not from a deb so I don't know how to get rid of it.

---

### Post by roharme on 2009-06-07
Is volume itself is down.

Are your player is muted

Not all codecs are compatible with all players

---

### Post by Sashin on 2009-06-08
I've checked if the sound is down, I don't think it was a codecs thing. No sound works, not from internet, not startup, not from music etc.

But ever since I installed that realtek thing I lost my sound, and some weird new sound device called "Via" was detected in volume controls.

I just need some way for everything to go back to the way it was one day ago.

---

### Post by tolotos on 2009-06-08
Was there some kind of readme or install.txt delivered along with the script? If so, this might indicate what has been changed, so that you could remove it manually.

---

### Post by Sashin on 2009-06-08
There's a readme, but there's no info on how to uninstall it.

> The source code copy from [www.alsa-project.org](www.alsa-project.org).      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC269
ALC272
ALC660
ALC660VD
ALC662
ALC663
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from [www.alsa-project.org](www.alsa-project.org).
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
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

### Post by Sashin on 2009-06-09
Bump!

---

### Post by Sashin on 2009-06-09
Another update: Earphones don't work either.

I would really appreciate if someone could fix this, I really don't want to have to reinstall.

---

