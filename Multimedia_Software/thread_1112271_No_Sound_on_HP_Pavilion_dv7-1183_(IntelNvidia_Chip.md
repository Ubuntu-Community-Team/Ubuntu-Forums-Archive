---
title: "No Sound on HP Pavilion dv7-1183 (Intel/Nvidia Chips)"
date: 2009-03-31
forum: Multimedia Software
---

### Post by california-ken on 2009-03-31
I hope that someone can help me get sound working on my HP dv7-1183d laptop running Ubuntu desktop 8.10.  I have spent hours searching web pages, installing new CD player software, updating ALSA drivers, etc.  So far, no success.

Key references for this forum item:
	 [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
	[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)
	[http://ubuntuforums.org/showthread.php?t=37406](http://ubuntuforums.org/showthread.php?t=37406)

HP Laptop specifics:
CPU – Intel Core2 Duo P7350 (64 bit)
PCI Bridge – Intel 82801 (ICH9) chipset
Audio Devices- HDA Digital PCBeep and HDA Intel sound card (as listed in Ubuntu's
Device Manager)
Under Windows (dual boot), sound works perfectly

Ubuntu sound settings:
	Devices – HDA Intel STAC92xx Analog  (OSS) This is the only setting that
	  produces test beep tones when “Test” is clicked

Symptoms:
	One loud BEEP on Ubuntu shutdown
	CD Players Rhythmbox, Exaile, Alsaplayer and Sound-Juicer advance 1 -2 seconds on an
	   audio track and then stop with no warning messages or sound produced.  All players display
	   all of the audio tracks on the CD.
	No sound on web video playback

System check results:
	aplay -l
		**** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI] 
  Subdevices: 1/1 
  Subdevice #0: subdevice #0
	lspci -v:
		**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

	sudo modeprobe snd- [TAB}
		FATAL: Module snd not found

ALSA drivers:
	Trying to Install module “HDA-Intel” from the ALSA 1.0.19 driver, lib and utils packages
I am stumped by the following section taken from the ALSA installation instructions for the HDA-Intel driver:
=======================================================================
Setting up modprobe and kmod support
Before you send a mail complaining that "I don't have /etc/&#8203;modules.conf, where do I find it ……" &#8210; the /etc/&#8203;conf.modules has been deprecated with a few distro's, but in your case it may still be /etc/&#8203;conf.modules. Basically they are both the same, but recent version of modutils use /etc/&#8203;modules.conf instead. Nothing to worry about as such, optionally please update to the latest version of modutils. This should solve your problem. 
Here's the example for this card. Copy and paste this to the bottom of your /etc/&#8203;modules.conf file. 
Note:* 
Debian GNU/Linux users need to save this information into a file in the /etc/&#8203;modutils/ directory (eg. /etc/&#8203;modutils/&#8203;alsa) and run update-modules.
Note also that the kernel module soundcore has been renamed in Debian kernels >2.6.23 into snd. A workaround is to put a symlink at /lib/modules/x.x.xx/kernel/sound/soundcore.ko pointing to snd.ko 

       # ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-hda-intel
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss
NB:* 
For drivers older than 0.9.0beta11 use: 
       snd-card-hda-intel

To copy and paste the above to your /etc/&#8203;modules.conf file follow these instructions. 

	I do not have a modules.conf or a conf.modules file in my /etc folder.
	I do not have a modutils folder in my /etc folder
	I have “soundcore.ko” in /lib/modules/2.6.27-11-generic/kernel/sound
	I have “snd.ko”  in /lib/modules/2.6.27-11-generic/kernel/sound/acore
	I do no know what a “symlink” is and whether it is necessary in my case.

I hope someone has solved the sound problem on the HP Pavioion dv7-1183d and can pass along the solution.
 I really need some help with this problem.  Thanks, in advance.

---

### Post by sambion on 2009-07-04
This seems like a long time for no reply. I hope it's not too late to get it solved. 
 I used the guide at this link:

[http://forum.notebookreview.com/showthread.php?t=331172]("http://forum.notebookreview.com/showthread.php?t=331172")

on my HP DV7 and it worked like a charm. The only difference is, is that I'm using 9.04.
 I don't see any changes that he describes that might make a difference between 8.04, 8.10, and 9.04.

I hope this helps and it isn't too late for you to get it working,
Sambion

Edit:
in his fix he tells you to edit :
/etc/modprobe.d/alsa-base
you need to edit:
/etc/modprobe.d/alsa-base.conf

that's the only thing I had to do differently to get my sound working great.

---

