---
title: "solved: no sound with ALSA on Gigabyte P35 DS3P, aka Realtek alc889a"
date: 2009-01-15
forum: Multimedia Software
---

### Post by oberueber on 2009-01-15
System is ubuntu 8.10

Board: Gigabyte P35 DS3P which uses Realtek alc889a 
Soundsystem: ALSA

Ok, I've read much in the forum, tried even more, no sucess at all.

After all I have the following state:
ALSA no sound

OSS => with sound, but therefore no sound on wine and no sound in flash player movies...

Nothing found at gigabyte, shame on you

So I decided to look at Realtek
=> download, Computer peripheral ICs, PC Audio Codecs, High definition audio Codecs, software

found: Linux driver (2.4 or 2.6)  vers 5.09	2008/11/28	4997k	

INstalled it with the script inside it, reboot my system
and what should I say
It works!!

After spending many hours to solve my problem I was overjoyed
** Thanks, Thanks to realtek  **

So if you are in the same situation give it a try and tell if it works to help other peoples

Bye and have sound !!

---

### Post by jothikumar on 2009-03-21
Hi,
    Initially i had sound with Hardy and then tried Compiz, something messed up and i lost sound. Tried the linux alsa driver from Realtek and it deleted some of the sound modules. So now i have upgraded to 8.10, still no sound.

From realtek website i have downloaded the driver 5.11 version and the Readme says, for ubuntu users do a manual install. I already tried the automatic install and screwed my system.

So can you please tell us the steps you followed and how did you get your sound working.

--thanks
Jothi

---

### Post by jothikumar on 2009-03-21
It is very hard to follow this Readme file

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



I have no modules.conf / modprobe.conf in the etc directory, i am using Interped (8.10)

---

### Post by OldMongrel on 2009-04-12
Newbie Alert! Other than fooling around briefly with Red Hat several years ago, this is all new to me.

I cannot get sound either. I downloaded the Realtek drivers and ran them as best I could as outlined in the included instructions (noted in above posts), but, as also noted, there is no...

/etc/modules.conf or /etc/modprobe.conf

...in 8.10. I also saw some messages scrolling by during MAKE about missing or incorrect parameters.

I have a new system on a Gigabyte MA780G-UD3H/Athlon-X2 7750 , which uses the Realtek ALC889A on-board sound. Kernel is 2.26.7.11-generic (64 bit).

Thanks, folks, and have a nice Easter and/or Sunday.

Oldmongrel

---

### Post by dannymichel on 2009-08-15
bump
how is this solved?
i dont see an answer

---

