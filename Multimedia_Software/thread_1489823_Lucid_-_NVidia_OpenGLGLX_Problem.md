---
title: "Lucid - NVidia OpenGL/GLX Problem"
date: 2010-05-21
forum: Multimedia Software
---

### Post by cryptotheslow on 2010-05-21
Hi,

Recent upgrade from karmic to lucid. I have an NVidia GTS250 GPU. I had to install the nvcurrent package via Synaptic as no drivers were showing in the Hardware Drivers section.

Hardware Drivers now says that the driver is Activated but not in use.

However lsmod disagrees:
```
graham@gt-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nvidia               9932176  28 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5259  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
it87                   17548  0 
hwmon_vid               2298  1 it87
asus_atk0110            9017  0 
parport_pc             25962  1 
i2c_piix4               8335  0 
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
vga16fb                11385  0 
ahci                   32008  0 
vgastate                8961  1 vga16fb
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
r8169                  33884  0 
mii                     4381  1 r8169
pata_atiixp             3148  2 
ati_agp                 5094  0 
agpgart                31724  2 nvidia,ati_agp

graham@gt-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0)
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce GTS 250] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

The main problem I have is that GLX appears to be borked. The NVidia X Server Settings app just reports:  "Fail to query the GLX server vendor." on the OpenGL/GLX Information tab.


glxinfo is equally as uninformative:
```
graham@gt-desktop:~$ glxinfo
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig
```


I really have no idea how to even start trying to fix this and Google is not being my friend on this one :(

Any ideas?

Thanks

---

### Post by ratcheer on 2010-05-21
This was a bug in the early versions of Lucid, but it should be fixed in the released version. The bug woul show that the driver was not currently in use, but it really was being used. So, it was really just misinformation, not a real problem.

Do you have an applet System >> Administration >> nVidia X Server Settings? If so, run it and your nVidia driver should be shown as in the attached picture. If not, get back to us.

Tim

---

### Post by cryptotheslow on 2010-05-21
Yes I have that applet. It is in there that the OpenGL/GLX info reports a problem - as well as glxinfo from a Terminal prompt.

This is an upgrade from karmic done today via Update Manager so should be bang up to date.

Screenshots attached to show what I mean :)

---

### Post by ratcheer on 2010-05-21
I don't know. I have never seen anything like that.

Sorry,
Tim

---

### Post by cryptotheslow on 2010-05-21
I have a horrible feeling there were some remnants of the manually installed driver from karmic left lingering around.

Any ideas what the OpenGL/GLX package names are? Maybe I can try purging and reinstalling them.

---

### Post by cryptotheslow on 2010-05-23
OK - I managed to solve this by purging the nvidia packages, blacklisting Nouveau (as it was still showing up in lsmod) and then installing the driver using the installer file from the NVidia site. Odd thing is that is the same version of the driver as gets installed via "Hardware Drivers" that doesn't work.

Thanks to Apewall for their instructions on post #10 of this thread
[http://ubuntuforums.org/showthread.php?t=1470343#10](http://ubuntuforums.org/showthread.php?t=1470343#10)

Followed those to the letter and all is now working - with the exception that the NVidia Settings applet does not appear in the Administration menu - not that I care, I never used to use it anyway and it can always be run manually.

---

