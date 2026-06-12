---
title: "Sound only working in integrated speakers, and not in headphones jack"
date: 2008-03-02
forum: Multimedia &amp; Video
---

### Post by Skald on 2008-03-02
Hello everyone and thanks in advance for any help you may provide.

I have a Acer TravelMate 4320 [like this]("http://www.acer.no/public/page4.do?link=oln56.redirect&dau22.ohttp://id=28989&UserCtxParam=0&GroupCtxParam=0&dctx1=12&CountryISOCtxParam=NO&LanguageISOCtxParam=no&ctx3=-1&ctx4=Norge&crc=2851775570"), which I recently installed Ubuntu on. Now not beeing a very experienced user on Ubuntu I cant understand the problem that has occured. The sound works pretty nicely in the integrated speakers but when I plug in my headphones in the front jack the sound stay in the speakers. I have already tried to switch in "sound" on the System-menu, but there I cant choose from anything else then the drivers (ALSA, OSS ++) and of course that does not work. I hope somone here can provide some help on this issue. And again, thanks in advance.

---

### Post by Metaljaz on 2008-03-02
Double click on the volume control button on the top right hand corner of the screen. Check to make sure you don't have the headphones muted.

---

### Post by Fonsis on 2008-03-03
This should work:

1. installed linux-backports-modules-generic by going to Synaptic

2. added 'options snd-hda-intel model=acer' to the last line in /etc/modprobe.d/alsa-base

3. Rebooted, and double clicked on speaker icon in system tray. Sliders for headphone volume now appear and external speakers now work. Internal speakers can be muted without affecting headphone volume by using the keyboard volume control.

[http://ubuntuforums.org/showthread.php?t=692485](http://ubuntuforums.org/showthread.php?t=692485)

---

### Post by Skald on 2008-03-04
Thanks for a really good answer. This was very helpful and the front jack now works as it should. Thank you very much, and Im sorry I didnt search this enough before I posted.

---

### Post by nutz on 2008-03-04
I have this issue on my Compaq F750us. Any ideas for me?

---

### Post by Skald on 2008-03-05
Did you try the guide Fonsis posted?

---

### Post by nutz on 2008-03-05
> **Skald said:**
> Did you try the guide Fonsis posted?


I did not because my sound card isn't Intel based.

---

### Post by nutz on 2008-03-05
I will post lspci...

---

### Post by nutz on 2008-03-05
nutz@nutz-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
nutz@nutz-laptop:~$

---

### Post by nutz on 2008-03-05
This is from /etc/modprobe.d/alsa-base


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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

