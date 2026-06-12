---
title: "usb microphone problem"
date: 2010-08-22
forum: Multimedia Software
---

### Post by borisclink on 2010-08-22
I have been trying for some time to migrate 100% from XP to Linux Mint 9, especially in respect of the video editing I do, because Ubuntu/Linux is better in almost every respect.  Voice-overs are, however, a problem because I can get my condenser microphone to work only partially (decent sound quality but an unacceptable level of hiss) and my USB microphone delivers no sound at all.  It is not even flagged in the PulseAudio options, although it appears to be mounted.
 Below are some of the details of the system.  I am sure some of this information is not relevant, because I am not knowledgeable enough to sort out the important bits.
 Please can anyone out there help.
 By the way, I'd be grateful if someone could not only tell me what to do, but also how to do it!
 

 Computer Name		SHUTTLE SP35P2
 

 Motherboard:
 CPU Type			2x Intel Pentium III Xeon, 2666 MHz (9 x 296)
 

 System Memory		3072 MB
 BIOS Type			Award (07/03/09 - SP35S20J
 

 [SIZE=4]**lspci **[/SIZE] 
 

 00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)  
 00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)  
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)  
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)  
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)  
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)  
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)  
 00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)  
 00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)  
 00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)  
 01:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9600 GT] (rev a1)  
 02:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller  
 03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)  
 04:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
 

 

  [SIZE=4]**uname -a **[/SIZE] 
 

 Linux Shuttle 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux
 

 

 [SIZE=4]**$ cat /proc/asound/version **[/SIZE] 
 

 Advanced Linux Sound Architecture Driver Version 1.0.23.  
 Compiled on Aug 17 2010 for kernel 2.6.32-21-generic-pae (SMP).  
 

 

 [SIZE=4]**$ lsusb **[/SIZE] 
 

 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 002: ID 0d8c:000e C-Media Electronics, Inc. Audio Adapter (Planet UP-100, Genius G-Talk)  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 003: ID 0bc2:3000 Seagate RSS LLC  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 

 

 [SIZE=4]**$ find /proc/asound/card***[/SIZE]  
 

 /proc/asound/card0  
 /proc/asound/card0/oss_mixer 
 /proc/asound/card0/id  
 /proc/asound/card0/codec#0 
 /proc/asound/card0/pcm2c 
 /proc/asound/card0/pcm2c/sub0 
 /proc/asound/card0/pcm2c/sub0/prealloc_max 
 /proc/asound/card0/pcm2c/sub0/prealloc 
 /proc/asound/card0/pcm2c/sub0/status 
 /proc/asound/card0/pcm2c/sub0/sw_params 
 /proc/asound/card0/pcm2c/sub0/hw_params 
 /proc/asound/card0/pcm2c/sub0/info 
 /proc/asound/card0/pcm2c/info 
 /proc/asound/card0/pcm1p 
 /proc/asound/card0/pcm1p/oss 
 /proc/asound/card0/pcm1p/sub0 
 /proc/asound/card0/pcm1p/sub0/prealloc_max 
 /proc/asound/card0/pcm1p/sub0/prealloc 
 /proc/asound/card0/pcm1p/sub0/status 
 /proc/asound/card0/pcm1p/sub0/sw_params 
 /proc/asound/card0/pcm1p/sub0/hw_params 
 /proc/asound/card0/pcm1p/sub0/info 
 /proc/asound/card0/pcm1p/info 
 /proc/asound/card0/pcm0c 
 /proc/asound/card0/pcm0c/oss 
 /proc/asound/card0/pcm0c/sub0 
 /proc/asound/card0/pcm0c/sub0/prealloc_max 
 /proc/asound/card0/pcm0c/sub0/prealloc 
 /proc/asound/card0/pcm0c/sub0/status 
 /proc/asound/card0/pcm0c/sub0/sw_params 
 /proc/asound/card0/pcm0c/sub0/hw_params 
 /proc/asound/card0/pcm0c/sub0/info 
 /proc/asound/card0/pcm0c/info 
 /proc/asound/card0/pcm0p 
 /proc/asound/card0/pcm0p/oss 
 /proc/asound/card0/pcm0p/sub0 
 /proc/asound/card0/pcm0p/sub0/prealloc_max 
 /proc/asound/card0/pcm0p/sub0/prealloc 
 /proc/asound/card0/pcm0p/sub0/status 
 /proc/asound/card0/pcm0p/sub0/sw_params 
 /proc/asound/card0/pcm0p/sub0/hw_params 
 /proc/asound/card0/pcm0p/sub0/info 
 /proc/asound/card0/pcm0p/info 
 /proc/asound/cards
 

 

 [SIZE=4]**$ cat /etc/modprobe.d/alsa-base.conf **[/SIZE]
 

 # autoloader aliases 
 install sound-slot-0 /sbin/modprobe snd-card-0 
 install sound-slot-1 /sbin/modprobe snd-card-1 
 install sound-slot-2 /sbin/modprobe snd-card-2 
 install sound-slot-3 /sbin/modprobe snd-card-3 
 install sound-slot-4 /sbin/modprobe snd-card-4 
 install sound-slot-5 /sbin/modprobe snd-card-5 
 install sound-slot-6 /sbin/modprobe snd-card-6 
 install sound-slot-7 /sbin/modprobe snd-card-7 
  
 # Cause optional modules to be loaded above generic modules 
 install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; } 
 # 
 # Workaround at bug #499695 (reverted in Ubuntu see LP #319505) 
 install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; } 
 install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; } 
 install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; } 
 # 
 install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; } 
 # Cause optional modules to be loaded above sound card driver modules 
 install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; } 
 install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; } 
  
 # Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) 
 install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; } 
 # Prevent abnormal drivers from grabbing index 0 
 options bt87x index=-2 
 options cx88_alsa index=-2 
 options saa7134-alsa index=-2 
 options snd-atiixp-modem index=-2 
 options snd-intel8x0m index=-2 
 options snd-via82xx-modem index=-2 
 options snd-usb-audio index=-2 
 options snd-usb-us122l index=-2 
 options snd-usb-usx2y index=-2 
 options snd-usb-caiaq index=-2 
 # Ubuntu #62691, enable MPU for snd-cmipci 
 options snd-cmipci mpu_port=0x330 fm_port=0x388 
 # Keep snd-pcsp from being loaded as first soundcard 
 options snd-pcsp index=-2

---

