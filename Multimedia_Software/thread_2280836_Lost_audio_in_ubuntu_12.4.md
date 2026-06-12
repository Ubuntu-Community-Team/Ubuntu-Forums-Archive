---
title: "Lost audio in ubuntu 12.4"
date: 2015-06-02
forum: Multimedia Software
---

### Post by gary59 on 2015-06-02
I have Ubuntu installed on an old HP Pavilion a700n .  I put a couple of gigs of ram in there and it ran really nice until about 2 weeks back and for some reason I lost audio. Not real sure what happened. To be honest, I think it was something in the updates that my computer did not like as I did not attempt to modify anything by myself. I had found two different threads on audio problems and was not able to resolve anything with them. 
If any one has had something similar happen and could offer any insight, I sure could use it.

---

### Post by Yellow Pasque on 2015-06-03
Try this first (resets user's pulseaduio config):
```
rm -r ~/.pulse*; pulseaudio -k
```

If it's still not working, get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by gary59 on 2015-06-03
Here is the result:  Failed to kill daemon: No such process
I should also say I am getting crash reports almost every time I try to open a tab in firefox. 
I went to the link, it resulted in this content. 
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Thu Jun  4 01:33:52 UTC 2015


!!Linux Distribution
!!------------------

Ubuntu 12.04.5 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 12.04.5 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu precise (12.04.5 LTS)"


!!DMI Information
!!---------------

Manufacturer:      HP Pavilion 061
Product Name:      PJ516AA-ABA A700N
Product Version:   0n81211RE101KELUT00
Firmware Version:   3.11


!!Kernel Information
!!------------------

Kernel release:    3.2.0-85-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         athlon
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.25
Utilities version:  1.0.25


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:11.5 0401: 1106:3059 (rev 60)
    Subsystem: 1043:810a


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---T 1 root audio 116,  1 Jun  3 11:35 /dev/snd/seq
crw-rw---T 1 root audio 116, 33 Jun  3 11:35 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:252: no soundcards found...

ARECORD

arecord: device_list:252: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
via
bnep
pppoe
vesafb
pppox
drm
ppdev
snd_page_alloc
soundcore
serio_raw
i2c_viapro
bluetooth
binfmt_misc
lp
mac_hid
parport_pc
shpchp
parport
firewire_ohci
usbhid
usb_storage
hid
via_rhine
firewire_core
crc_itu_t
pata_via
sata_via


!!ALSA/HDA dmesg
!!--------------

---

### Post by Yellow Pasque on 2015-06-03
```
Driver version: 
```
^The kernel module is not even loading. Try loading the module manually:
```
sudo modprobe -v snd-via82xx
```

Other things to try:
- Reinstall kernel package:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```
Then reboot.
- If that doesn't help, try booting into the previous kernel

---

### Post by gary59 on 2015-06-03
gary@gary-PJ516AA-ABA-A700N:~$ sudo modprobe -v snd-via82xx
[sudo] password for gary: 
install /sbin/modprobe --ignore-install snd  && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/snd.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/seq/snd-seq-device.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/snd-timer.ko 
install /sbin/modprobe --ignore-install snd-seq  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/seq/snd-seq.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/seq/snd-seq-midi-event.ko 
install /sbin/modprobe --ignore-install snd-rawmidi  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/snd-rawmidi.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/seq/snd-seq-midi.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko 
install /sbin/modprobe --ignore-install snd-pcm  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
insmod /lib/modules/3.2.0-85-generic/kernel/sound/core/snd-pcm.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/sound/ac97_bus.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko 
insmod /lib/modules/3.2.0-85-generic/kernel/drivers/input/gameport/gameport.ko 
install /sbin/modprobe --ignore-install snd-via82xx  && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }
insmod /lib/modules/3.2.0-85-generic/kernel/sound/pci/snd-via82xx.ko 
gary@gary-PJ516AA-ABA-A700N:~$

---

### Post by gary59 on 2015-06-03
Reloaded manually, firefox crashed. On the restart, I tried to use "rhythmbox", and it works !!! First time I have heard music on of this computer in about 2 weeks now !

---

### Post by gary59 on 2015-06-03
Reloaded manually, firefox crashed. On the restart, I tried to use "rhythmbox", and it works !!! First time I have heard music on of this computer in about 2 weeks now !

---

### Post by gary59 on 2015-06-03
have music! machine freezing . will reboot and try again. On Rebooting, I had no sound, but when I used the command for manual reload it came back. Now in the process of attempting to reinstall the kernel package. Can not thank you enough, was so damn neat to have sound again.

---

### Post by gary59 on 2015-06-03
I can hear you tube videos again, and I can hear my local radio station again. Thank you very much.

---

### Post by Yellow Pasque on 2015-06-03
^You're welcome. I was wondering whether the firefox freezing started at the same time you lost sound.

---

### Post by gary59 on 2015-06-04
Yes, it was the case. All was fine prior to that.  I think one of the updates about 2 weeks back was incompatible with this rather old machine.

---

### Post by gary59 on 2015-06-04
When i try to reinstall kernel package, this is what I get : gary@gary-PJ516AA-ABA-A700N:~$ sudo apt-get install --reinstall linux-image-`uname -r`
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
gary@gary-PJ516AA-ABA-A700N:~$

---

### Post by Yellow Pasque on 2015-06-04
Obviously, you have to make sure all other package management programs (Software Center, synaptic, etc.) are closed. If you're still getting that error, then you have a stale lock file.
Run all three commands, even if one of them complains about a missing file:
```
sudo rm /var/lib/apt/lists/lock 
sudo rm  /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```

Then, see if there are any updates available:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by gary59 on 2015-06-04
gary@gary-PJ516AA-ABA-A700N:~$ sudo rm /var/lib/apt/lists/lock 
[sudo] password for gary: 
gary@gary-PJ516AA-ABA-A700N:~$ sudo rm  /var/cache/apt/archives/lock
gary@gary-PJ516AA-ABA-A700N:~$ sudo rm /var/lib/dpkg/lock
gary@gary-PJ516AA-ABA-A700N:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                    
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [196 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:7 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,178 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [54.3 kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed Release [196 kB]           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [490 kB]      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en            
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,981 B]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [119 kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [9,726 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [950 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.6 kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [275 kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [16.7 kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [10.6 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [7,613 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [7,297 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [8,333 B]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources [130 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Sources [3,759 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Sources [42.1 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Sources [2,198 B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [555 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted i386 Packages [8,939 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe i386 Packages [129 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse i386 Packages [2,865 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex [208 B]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse TranslationIndex [199 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted TranslationIndex [202 B]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe TranslationIndex [205 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted i386 Packages [1,138 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main i386 Packages [206 kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse i386 Packages [28 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe i386 Packages [8,947 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main TranslationIndex [10.6 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse TranslationIndex [7,613 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted TranslationIndex [7,297 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe TranslationIndex [8,333 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [158 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Translation-en 
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Translation-en [75.9 kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/main Translation-en [42.7 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/restricted Translation-en    
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-proposed/universe Translation-en [5,611 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Fetched 3,770 kB in 18s (206 kB/s)                                             
Reading package lists... Done
gary@gary-PJ516AA-ABA-A700N:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
gary@gary-PJ516AA-ABA-A700N:~$

No audio on reboot , until I use "
sudo modprobe -v snd-via82xx"  
Then I get audio again. 
The machine has not crashed on me yet this morning and I can use audio again. Have to say it is much much nicer than it was. 
Thank you much for your time and thought.

---

### Post by Yellow Pasque on 2015-06-04
It's possible the alsa init/upstart job is crashing on startup (I've seen it many times before). Does this give any output?
```
dmesg | grep -i alsa
```

---

### Post by gary59 on 2015-06-04
gary@gary-PJ516AA-ABA-A700N:~$ dmesg | grep -i alsa
[   14.589149] init: alsa-restore main process (951) terminated with status 19
gary@gary-PJ516AA-ABA-A700N:~$ 
gary@gary-PJ516AA-ABA-A700N:~$

---

### Post by Yellow Pasque on 2015-06-05
Did you try booting to the previous kernel?

---

### Post by gary59 on 2015-06-06
No, that is something that I have not done yet. Need to spend time reading how it is done.

---

### Post by gary59 on 2015-06-10
To anyone who wants to know : I did not figure out how to get into an earlier kernel, but I am able to hear sound OK if Just run this string when I start up : 
sudo modprobe -v snd-via82xx . Now I know this is not quite as it should be, but it seems real nice after no audio. I would sure like thank the most kind person who gave me assistance.

---

