---
title: "no sound on Ubuntu 8,10"
date: 2009-01-02
forum: Multimedia Software
---

### Post by Gunch36 on 2009-01-02
hi everyone!
i run Ubuntu 8.10 for 2 months now and i love it, just now i have a problem.  my  sound stoped to work.   I was listening to music with Amarok and when i was away from my keyboard the sound disappeared and i can not figure out how to get it back.
and here is LSPCI for my PC:

00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by linux_tech on 2009-01-02
try to restart alsa

```

sudo /etc/init.d/alsa-utils stop

sudo alsa force-reload

sudo /etc/init.d/alsa-utils start



```

---

### Post by Gunch36 on 2009-01-02
it doese not work: here is how it looks like on terminal:
[QUOTE]guntars@guntars-laptop:~$ sudo /etc/init.d/alsa-utils stop
[sudo] password for guntars: 
 * Shutting down ALSA...                                                 [ OK ] 
guntars@guntars-laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/guntars/.gvfs
      Output information may be incomplete.
Terminating processes: 6940 7108lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/guntars/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/guntars/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/guntars/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
guntars@guntars-laptop:~$ sudo /etc/init.d/alsa-utils start
  * Setting up ALSA...                                                                            [ OK ]

---

### Post by Coder543 on 2009-01-02
Make sure in the Volume Control panel the PCM and Front are both maxed out. You could also go to synaptic and mark alsa-base for reinstallation then click apply and see if that fixes it. Also, make sure you have rebooted since the time that this happened.

---

### Post by /carlito on 2009-01-02
You should check "System => Preferences => Sound" and do the tests to see if it produces any output. If it doesn't try switching over to OSS. 

Note: Using OSS (emulation) is NO solution as it has been deprecated some time ago. If this step restores your sound output you should obtain a copy of alsaconf so you can succesfully restore ALSA to its working state.

---

### Post by Gunch36 on 2009-01-04
alsa-base reinstitution helped ... tnx!

---

### Post by Doncr on 2009-02-03
Don't know if this is what worked or if it was - er - plugging the audio cable back in :redface:

---

