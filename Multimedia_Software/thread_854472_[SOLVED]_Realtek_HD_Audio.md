---
title: "[SOLVED] Realtek HD Audio"
date: 2008-07-09
forum: Multimedia Software
---

### Post by Rich930 on 2008-07-09
Hey, i have a Realtek HD Audio card, but i haven't got any sound :D

I downloaded the tar off of realteks website, but no luck. ANyone know how i get sound outta this thing?

Many thanks.

---

### Post by Rich930 on 2008-07-10
anyone?

---

### Post by lazertek on 2008-07-10
> **Rich930 said:**
> anyone?
try typing in alsamixer and check volume levels on there first...  see if that's what the prob is...

---

### Post by danwood76 on 2008-07-10
Realtek HD audio covers a huge range of sound cards.
Most of which are supported by ALSA.

Each chipset has various settings that can be tweaked in order to get them working, first we need to know which soundcard you have.

Open up a terminal (Applications -> Accesories -> Terminal) and run this command and post the output:
```

lspci | grep -i 'Audio'

```

There is also a good guide to troubleshooting sound in the community docs:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by Rich930 on 2008-07-11
hey sorry for the late reply. The wireless is playing up again in linux but not windows so i have no idea whats going on, but heres the output of that command:

```
00:09.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:09.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller


```

---

### Post by danwood76 on 2008-07-11
Ok we need to find out exactly which type of card you have, the card above is very generic (the SIS one)

This command might give a better indication:
```

cat /proc/asound/cards

```

---

### Post by th1bill on 2008-07-11
[COLOR="DarkRed"]I'm not an Ubuntu expert but I had the same problem on my Biostar K8M800 motherboard w/AC97 audio built in.  The problem is not the driver from Realtech but is in the Kernal update.  The last number in my updated kernal is 19 and the one before that was 16.  In the GRUB, at boot, I have the option to boot into either kernal and on booting into the older version my sound is restored.

I believe the folks at Ubuntu will have this repaired very quickly but for the time this worked on my unit and it should on others as well.[/COLOR]

---

### Post by Rich930 on 2008-07-12
> **danwood76 said:**
> Ok we need to find out exactly which type of card you have, the card above is very generic (the SIS one)

This command might give a better indication:
```

cat /proc/asound/cards

```



here it is:

```
 0 [SIS966         ]: HDA-Intel - HDA SIS966
                      HDA SIS966 at 0xfebfc000 irq 20

```

---

### Post by danwood76 on 2008-07-13
Follow the steps on this community page:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I would update alsa to the latest version and then try sepcifying module parameters.

---

### Post by Rich930 on 2008-07-13
hey, i followed the steps on that link u gave me, but when i get to the part where it says: 

"Compile and install alsa-driver 

cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)"

I get this:
```
wardy@wardy-desktop:/wardy/src/alsa/alsa-driver-1.0.14$ sudo ./configure --with-cards=hda-intel --with-kernel=/wardy/src/linux-headers-$(uname -r)
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /wardy/src/alsa/alsa-driver-1.0.14
checking cross compile... 
checking for directory with kernel source... /wardy/src/linux-headers-.6.24-19-generic
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /wardy/src/linux-headers-.6.24-19-generic/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/2.6.24-19-generic/build).


```

please help! 

Thanks.

---

### Post by danwood76 on 2008-07-14
You need to install a couple of packages that allow you to compile kernel stuff.
To do so run this:
```

sudo apt-get install build-essential kernel-headers-$(uname -r)

```

You dont actually need to specify the kernel in that build line as it uses the current kernels header files anyway so the line should just be:
```

sudo ./configure --with-cards=hda-intel

```
The only reason why you would specify the kernel is if you are cross compiling for a different kernel version.

So make sure those packages are installed and then run the command above in place of the one you tried.

---

### Post by Rich930 on 2008-07-14
oh ok thanks, i will try later, will let you know. :)

---

### Post by Rich930 on 2008-07-27
hey sorry for the late raply , but it keeps givinig me an error when i try "sudo make" :

```
wardy@wardy-desktop:/wardy/src/alsa/alsa-driver-1.0.14$ sudo make
make dep
make[1]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/acore'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/ioctl32'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/ioctl32'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/oss'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/oss'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/seq'
make[4]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/seq/instr'
make[4]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/seq/instr'
make[4]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/seq/oss'
make[4]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/seq/oss'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/acore/seq'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/acore'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/i2c'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/i2c/other'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/i2c/other'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/i2c'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/mpu401'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/mpu401'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/opl3'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/opl3'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/opl4'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/opl4'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/pcsp'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/pcsp'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/vx'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers/vx'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/drivers'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/ad1816a'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/ad1816a'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/ad1848'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/ad1848'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/cs423x'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/cs423x'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/es1688'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/es1688'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/gus'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/gus'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/msnd'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/msnd'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/opti9xx'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/opti9xx'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/sb'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/sb'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/wavefront'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa/wavefront'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/isa'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/synth'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/synth/emux'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/synth/emux'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/synth'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ac97'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ac97'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ali5451'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ali5451'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/asihpi'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/asihpi'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/au88x0'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/au88x0'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ca0106'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ca0106'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/cs46xx'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/cs46xx'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/cs5535audio'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/echoaudio'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/echoaudio'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/emu10k1'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/emu10k1'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/hda'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/hda'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ice1712'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ice1712'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/korg1212'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/korg1212'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/mixart'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/mixart'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/nm256'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/nm256'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/pcxhr'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/pcxhr'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/pdplus'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/pdplus'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/riptide'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/riptide'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/rme9652'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/rme9652'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/trident'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/trident'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/vx222'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/vx222'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ymfpci'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci/ymfpci'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pci'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/codecs'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/codecs'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/core'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/core'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/fabrics'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/fabrics'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/soundbus'
make[4]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa/soundbus'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/aoa'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/soc'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/at91'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/at91'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/codecs'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/codecs'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/pxa'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/pxa'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/s3c24xx'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/sh'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/soc/sh'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/soc'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/usb'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/usb/caiaq'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/usb/caiaq'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/usb/usx2y'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/usb/usx2y'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/usb'
make[2]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pcmcia'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pcmcia/pdaudiocf'
make[3]: Entering directory `/wardy/src/alsa/alsa-driver-1.0.14/pcmcia/vx'
make[3]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pcmcia/vx'
make[2]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14/pcmcia'
make[1]: Leaving directory `/wardy/src/alsa/alsa-driver-1.0.14'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/wardy/src/alsa/alsa-driver-1.0.14  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/wardy/src/alsa/alsa-driver-1.0.14/acore/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [/wardy/src/alsa/alsa-driver-1.0.14/acore] Error 2
make[1]: *** [_module_/wardy/src/alsa/alsa-driver-1.0.14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2

```

 :P

---

### Post by Rich930 on 2008-07-27
so when i try "sudo make install" it wont let me.

---

### Post by danwood76 on 2008-07-27
Well that version of alsa is outdated some what.
Try compiling the latest version (1.0.17) you wont get better results from that earlier version anyway.

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)

If you still get the same error with the latest version you will need to edit the makefile.
Post back if you still get the same error.

---

### Post by Rich930 on 2008-07-27
hey ive got it working! :D

only problem is now though is that i have 3 jacks required for my speakers 
1 for center / sub,
1 for front L & R,
1 for Rear L & R.

So atm, im only using one cable which i think is stereo but its only coming out of the center and front and rear Left, none of the two right speakers, weird?

So is there an interface which lets me configure which jack is which output?

---

### Post by danwood76 on 2008-07-27
So did recompiling the drivers give you sound out?

Well if all the volume controls are set high on the gnome volume control then this could be caused by the alsa driver module options.
There are several different options which tell alsa how the soundcard is setup.

First we need to know which codec is being used on your card: (Post the output here)
```

cat /proc/asound/card0/codec#* | grep Codec

```
Then from this we can lookup that codec on the alsa list to see whcat options are available.

---

### Post by Rich930 on 2008-07-28
here it is:

```
wardy@wardy-desktop:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC880

```

---

### Post by danwood76 on 2008-07-28
Ok, so from the ALSA-Configuration.txt file we can see there are quite a few options to choose from:

```

		  Model name	Description
		  ----------    -----------
		ALC880
		  3stack	3-jack in back and a headphone out
		  3stack-digout	3-jack in back, a HP out and a SPDIF out
		  5stack	5-jack in back, 2-jack in front
		  5stack-digout	5-jack in back, 2-jack in front, a SPDIF 
		  6stack	6-jack in back, 2-jack in front
		  6stack-digout	6-jack with a SPDIF out
		  w810		3-jack
		  z71v		3-jack (HP shared SPDIF)
		  asus		3-jack (ASUS Mobo)
		  asus-w1v	ASUS W1V
		  asus-dig	ASUS with SPDIF out
		  asus-dig2	ASUS with SPDIF out (using GPIO2)
		  uniwill	3-jack
		  fujitsu	Fujitsu Laptops (Pi1536)
		  F1734		2-jack
		  lg		LG laptop (m1 express dual)
		  lg-lw		LG LW20/LW25 laptop
		  tcl		TCL S700
		  clevo		Clevo laptops (m520G, m665n)
		  test		for testing/debugging purpose, almost all controls can be
				adjusted.  Appearing only when compiled with
				$CONFIG_SND_DEBUG=y
		  auto		auto-config reading BIOS (default)

```
You basically need to pick one that is closest to (or the same as) your setup.

From what you've said I would guess that yours is a 6stack variety (generally 5.1 surround sound cards are 6stack)

So we can add this option to the module options like so:

First open up the alsa config file so we can edit it:
```

sudo gedit /etc/modprobe.d/alsa-base

```
Scroll right to the bottom of the file and add this:
```

options snd-hda-intel model=6stack

```
Also you need to check there arent any other lines starting with 'options snd-hda-intel' if there are then delete them.

Save the file and then reboot and test your sound again.
If its still not correct re open that alsa-base file and change the model to another one from that list I posted.

---

### Post by Rich930 on 2008-07-28
:OOOOOO  

XD

DUDE!!

I love you!!! :D :P

its all working fine now! i channelled all the speakers just fine and the input from my xbox works! XD

I cant thankyou enough - i am so grateful! XD
Thankyou soo much :D :P lol

I actually have 6stack-digout. but i don tuse the spdif.
but thankss again - your amazing :D
-------------------------------------

One more question,, do you know how i can forward / share my internet with my xbox?
cheers.

---

### Post by danwood76 on 2008-07-28
No probs.

Now you have sound working to get the perfect and most useful audio setup I would follow this guide:
[http://ubuntuforums.org/showthread.php?t=776739&highlight=sound+pulseaudio](http://ubuntuforums.org/showthread.php?t=776739&highlight=sound+pulseaudio)

You can do some pretty sweet things with pules so its worth a look.

About your Xbox, I'm not really sure I would look at setting up a network bridge or a more advanced NAT setup.
You should be able to get a descent setup.

A quick search revealed a couple of threads:
[http://ubuntuforums.org/showthread.php?t=869207&highlight=Xbox+network+bridge](http://ubuntuforums.org/showthread.php?t=869207&highlight=Xbox+network+bridge)
[http://ubuntuforums.org/showthread.php?t=867678](http://ubuntuforums.org/showthread.php?t=867678)

Ps.
Please mark the thread solved using thread tools ;)

---

### Post by Rich930 on 2008-07-29
yeah thanks again - i got my xbox working last night with firestarter. :D

---

