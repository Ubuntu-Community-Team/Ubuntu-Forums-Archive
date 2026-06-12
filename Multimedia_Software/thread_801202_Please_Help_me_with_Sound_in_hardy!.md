---
title: "Please Help me with Sound in hardy!"
date: 2008-05-20
forum: Multimedia Software
---

### Post by zeny on 2008-05-20
Hello!

Using 8.04 I have no - zip - zero sound! I'm using the On Board sound ICH9 I believe! Came with the Asus-p5k board, I've tried a few things from searching the forums but I think I've completely broke it! I'm using the Coax (Digital) output, and using 5.1 surround sound. 

I've done so many things, but this is the last: 

1. I think I reinstalled alsa
2. I tried installing the RealTek driver manually
From this thread ([http://ubuntuforums.org/showthread.php?t=673943&highlight=ICH9](http://ubuntuforums.org/showthread.php?t=673943&highlight=ICH9))
However, I get this error while doing 'make' 
> make[3]: Leaving directory `/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f/pcmcia/vx'
make[3]: Leaving directory `/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f/pcmcia/vx'
make[2]: Leaving directory `/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f/pcmcia'
make[1]: Leaving directory `/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f'
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f/acore/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[2]: *** [/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f/acore] Error 2
make[1]: *** [_module_/home/riban/realtek-linux-audiopack-RHEL4U4-4.05f/alsa-driver-1.0.12-RHEL4U4-4.05f] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [compile] Error 2


Thats just a sniplet of the output! I don't really know what I'm doing wrong

---

### Post by zeny on 2008-05-20
This goes through my trouble shooting steps: 

> 
riban@rounz:~$ aplay -l
aplay: device_list:205: no soundcards found...


> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Unknown device 829f
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


>  + HDA Intel driver
   - hda_intel: increase maximum DMA buffer size to 1024MB
   - hda_intel: add ATI RS690 HDMI audio support
   - hda-intel - Add check of MSI availabity
   - hda-intel - Disable MSI support as default
   - hda-intel - Disable INTX when MSI is used
   - Audio: Add nvidia HD Audio controllers of MCP67 support to hda_intel.c
   - hda_intel: ALSA HD Audio patch for Intel ICH9
-http://www.alsa-project.org/main/index.php/Changes_v1.0.13_v1.0.14rc1


Then

> riban@rounz:~$ sudo modprobe snd-hda-intel 
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


I then Followed this guide: 
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

...I'm going to reboot lets see the results :D

After Reboot: 

> riban@rounz:~$ aplay -l


********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 0: OSS ID [HD Audio front]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 1: OSS ID [HD Audio rear]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 2: OSS ID [HD Audio center/LFE]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 3: OSS ID [HD Audio side]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 4: OSS ID [HD Audio pcm4]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 5: OSS ID [HD Audio spdif-out]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 6: OSS ID [High Definition Audio rec1]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 1: snd_ctl_card_info_get_id [Intel HD Audio], device 7: OSS ID [High Definition Audio rec2]
  Subdevices: 1/1
  Subdevice #0: OSS subname


Still no sound I get this 

> 
audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample !
gconfaudiosink: Failed to connect steam:
Invalid argument


That happens when I go to "test" under System>Preferences>Sound

now I'm stuck!

---

### Post by zeny on 2008-05-20
I get this now, after trying both methods to install the drivers 

> riban@rounz:/usr/src/modules/alsa-driver$ sudo modprobe snd-hda-intel 
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-16-generic/updates/alsa/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.24-16-generic/updates/alsa/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)


---

### Post by zeny on 2008-05-21
Have I provided enough information? Anyone have any suggestions?

---

### Post by zeny on 2008-05-22
FIXED: I reinstalled Hardy, then from there I made sure all the volume was up on each and every option, so it works out one of my 5 speakers now. I don't know why this didn't work before because I did this last time too, I think the only difference is this time after the reinstall I upgraded everything right away then started installing stuff :)

---

### Post by BlkPhoenix on 2008-05-22
Great job. The simplest things are usually the ones that slip you. I'm using a Dell Inspiron 1420 laptop running Kubuntu. I went to the Kmixer and selected "Front". From there I pushed the volume icon to the max and sound was there!! :-)

---

### Post by zeny on 2008-05-22
=\ Now I gotta try and get 5.1 Surround working, but I've been reading and tried a few things, I don't think it will work. I haven't read any threads yet where someone got Optical IEC958 working with 5.1 yet. 

:D

---

