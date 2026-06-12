---
title: "no sound in 8.04 or 9.04"
date: 2009-05-16
forum: Multimedia Software
---

### Post by karen1000 on 2009-05-16
I don't know what to try next.  Sound card is enable in bios, nothing is muted, it recognizes the sound card and drivers (at least as far as I can tell.  Please help!  I an really new at this and I may have made some simple error. 
Some additional info is posted below:

  	 	 	 	 	 	  Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"   !!Kernel Information !!------------------  Kernel release:    2.6.28-11-generic Operating System:  GNU/Linux Architecture:      i686 Processor:         unknown SMP Enabled:       Yes   !!ALSA Version !!------------  Driver version:     1.0.18rc3 Library version:    1.0.18 Utilities version:  1.0.18   !!Loaded ALSA modules !!-------------------  snd_intel8x0   !!Sound Servers on this system !!----------------------------  Pulseaudio:       Installed - Yes (/usr/bin/pulseaudio)       Running - Yes  ESound Daemon:       Installed - Yes (/usr/bin/esd)       Running - No   !!Soundcards recognised by ALSA !!-----------------------------   0 [ICH5           ]: ICH4 - Intel ICH5                       Intel ICH5 with AD1980 at irq 17   !!PCI Soundcards installed in the system !!--------------------------------------  00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)  

 

 

 

     
 

 1317   Module snd-intel8x0m
 

 1318   --------------------
 

 1319  
 

 1320     Module for Intel ICH (i8x0) chipset MC97 modems.
 

 1321                         * Intel i810/810E, i815, i820, i830, i84x, MX440
 

 1322                                 ICH5, ICH6, ICH7
 

 1323                         * SiS 7013 (SiS 735)
 

 1324                         * NVidia NForce, NForce2, NForce2s, NForce3
 

 1325                         * AMD AMD8111
 

 1326                         * ALi m5455
 

 1327  
 

 1328     ac97_clock    - AC'97 codec clock base (0 = auto-detect)
 

 1329  
 

 1330     This module supports one card and autoprobe.
 

 1331  
 

 1332     Note: The default index value of this module is -2, i.e. the first
 

 1333           slot is excluded.
 

 1334  
 

 1335     The power-management is supported.
 

 1336  
 

 

 

 Could it be the sound daemon?

 

 

 

 

 gnome-settings-daemon 
  
 ** (gnome-settings-daemon:5470): WARNING **: Failed to acquire org.gnome.SettingsDaemon

---

