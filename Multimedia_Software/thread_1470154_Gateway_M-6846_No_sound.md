---
title: "Gateway M-6846 No sound"
date: 2010-05-02
forum: Multimedia Software
---

### Post by barkeep42 on 2010-05-02
Hello. Im new to Linux, just installed Lucid Lynx yesterday.
So far, I've had very few issues, except that I can't get sound at all. This applies to any program, and both speakers & headphones.

The sound is definitely not muted, and my settings in alsamixer seem fine. My profile is definitely an administrator.

When I run lshw -short, I get this:

WARNING: you should run this program as super-user.
H/W path           Device      Class       Description
======================================================
                               system      Computer
/0                             bus         Motherboard
/0/0                           memory      3954MiB System memory
/0/1                           processor   Intel(R) Core(TM)2 Duo CPU     T5550 
/0/100                         bridge      Mobile PM965/GM965/GL960 Memory Contr
/0/100/2                       display     Mobile GM965/GL960 Integrated Graphic
/0/100/2.1                     display     Mobile GM965/GL960 Integrated Graphic
/0/100/1a                      bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1a.1                    bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1a.7                    bus         82801H (ICH8 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801H (ICH8 Family) HD Audio Control
/0/100/1c                      bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1c/0        wlan0       network     PRO/Wireless 3945ABG [Golan] Network 
/0/100/1c.2                    bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1c.5                    bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1c.5/0      eth0        network     RTL8101E/RTL8102E PCI Express Fast Et
/0/100/1d                      bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1d.1                    bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1d.2                    bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1d.7                    bus         82801H (ICH8 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1f                      bridge      82801HEM (ICH8M) LPC Interface Contro
/0/100/1f.1        scsi0       storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE Cont
/0/100/1f.1/0.0.0  /dev/cdrom  disk        DVDRAM GSA-T20F
/0/100/1f.2                    storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA AHC
/0/100/1f.3                    bus         82801H (ICH8 Family) SMBus Controller
/1                 scsi5       storage

Any advice would be really appreciated!:confused:

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by barkeep42 on 2010-05-02
Linux zak-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
 

 

 **** List of PLAYBACK Hardware Devices **** 
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0 
 card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital] 
   Subdevices: 1/1 
   Subdevice #0: subdevice #0
 

 

 Advanced Linux Sound Architecture Driver Version 1.0.21.
 

 

 ==> /proc/asound/card0/codec#0 <== 
 Codec: SigmaTel STAC9205 
  
 ==> /proc/asound/card0/codec#1 <== 
 Codec: LSI ID 1040

---

### Post by lidex on 2010-05-02
OK. Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel enable_msi=0 model=eapd 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by barkeep42 on 2010-05-02
under System>Preferences>Sound, should "Intel HDA" be an option? If not, what should I be looking for?

---

### Post by lidex on 2010-05-02
> **barkeep42 said:**
> under System>Preferences>Sound, should "Intel HDA" be an option? If not, what should I be looking for?

Yes. From your previous post:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

---

### Post by barkeep42 on 2010-05-03
Ah, ok. This may be the problem then.

The only device listed is labeled "Internal Audio", and the rest of the description changes based on what I select in the "Profile" settings (Digital Stereo Duplex, etc) . 

Is there a way to make it find my device, manually or otherwise?

Thanks for all of your help so far!:)

---

