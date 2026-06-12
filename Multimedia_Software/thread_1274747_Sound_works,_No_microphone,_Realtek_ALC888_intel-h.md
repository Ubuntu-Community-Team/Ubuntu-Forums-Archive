---
title: "Sound works, No microphone, Realtek ALC888 intel-hda"
date: 2009-09-24
forum: Multimedia Software
---

### Post by Crystufer on 2009-09-24
Just installed Ubuntu a couple days ago. Got sound output working well enough, but the microphone seems to go into the codec and back out the speakers instead of into the software.
I found out it's an Intel HDA onboard sound card, so I go to this post right here.
[HDA Intel Sound Howto(Link)]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
and this does not work for me. Then I see the last bit at the bottom. The part that says to get the Realtek Alsa Driver, so I go there. I download it, and then I don't know how to work it. The readme says to do install manually, but the instructions are poorly translated and I don't know how to do STEP 2. It has no line of code to help me, and the instruction is not in newbie, so someone wanna help me out with a step by step of what they're trying to get me to do?

My Sound Codec:
```
cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC888
```

[My Motherboard(Link)]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2847&ProductName=GA-EP43-DS3L")

The output of My Device manager:
```
Model:      82801JI (ICH10 Family) HD Audio Controller
Vendor:     Intel Corporation (Giga-byte Technology)
Connection: PCI (Peripheral Component Interconnect)
```

---

### Post by raboofje on 2009-09-25
> **Crystufer said:**
> The readme says to do install manually, but the instructions are poorly translated and I don't know how to do STEP 2. It has no line of code to help me, and the instruction is not in newbie, so someone wanna help me out with a step by step of what they're trying to get me to do?

What does the README say? What is 'step 2'?

---

### Post by Crystufer on 2009-09-28
```
The source code copy from www.alsa-project.org.      ver:3.3-4
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
This Source Code is from www.alsa-project.org.
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
	6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the www.alsa-project.org, then unzip and install them. 
	   b. Suggest use "alsamixer" to control mixer function.
	   c. Used "alsaconf" can autodetect which drive you need to install (step 4). 	
        7. SUSE Distribution must install the ncurses package. 
```

You know, I spent half an hour writing that first post. I knew I'd miss some vital piece of info.

---

### Post by patmalcolm91 on 2009-10-28
Don't know if you've figured this out yet, but it simply means to turn on the "soundcore" kernel module, which is by default on anyways. If you want to double-check, you can enter:

```
lsmod | grep -i soundcore
```

If this command doesn't print anything to the screen, soundcore is not installed by default, and I don't know how you'd go about changing that. If, however, you get something like "soundcore               9088  1 snd", you're set.

---

