---
title: "Sound only works sometimes on boot"
date: 2008-12-15
forum: Multimedia Software
---

### Post by wmorgan on 2008-12-15
Sometimes sound works when I boot, sometimes it doesn't. I think the problem is due to some nondeterminism in the boot process, and I think these are the relevant pieces of my dmesg output, first when sound doesn't work, and then when sound does. Notice the line that says that no codecs are initialized for hda-intel in the first output. I can post the output of my aplay, lspci, etc, for both cases, if anyone thinks that they'll be useful.

WHEN SOUND DOESN'T WORK:
...
[   11.980532] ACPI: Power Button (FF) [PWRF]
[   11.980610] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   12.012526] ACPI: Power Button (CM) [PWRB]
[   12.593692] ACPI: WMI: Mapper loaded
[   12.743183] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.834403] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.879510] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   13.125993] nvidia: module license 'NVIDIA' taints kernel.
[   13.379964] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 21
[   13.379971] nvidia 0000:02:00.0: PCI INT A -> Link[AIGP] -> GSI 21 (level, low) -> IRQ 21
[   13.379977] nvidia 0000:02:00.0: setting latency timer to 64
[   13.380469] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   13.461250] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   13.461263] rt61pci 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   13.469103] phy0: Selected rate control algorithm 'pid'
[   13.737748] Registered led device: rt61pci-phy0:radio
[   13.737765] Registered led device: rt61pci-phy0:assoc
[   13.857738] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   13.857743] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[   13.857761] HDA Intel 0000:00:07.0: setting latency timer to 64
[   13.888275] hda-intel: no codecs initialized
[   13.888311] HDA Intel 0000:00:07.0: PCI INT A disabled
[   14.665213] lp: driver loaded but no devices found
[   14.814958] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k
[   15.378170] EXT3 FS on sda1, internal journal
[   16.318036] type=1505 audit(1228959965.806:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4737
[   16.457483] type=1505 audit(1228959965.946:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4742
[   16.457652] type=1505 audit(1228959965.946:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4742
...

WHEN SOUND WORKS:
...
[   10.984040] ACPI: Power Button (FF) [PWRF]
[   10.984128] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   11.016043] ACPI: Power Button (CM) [PWRB]
[   11.725732] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 21
[   11.725738] HDA Intel 0000:00:07.0: PCI INT A -> Link[AAZA] -> GSI 21 (level, low) -> IRQ 21
[   11.725756] HDA Intel 0000:00:07.0: setting latency timer to 64
[   11.738989] ACPI: WMI: Mapper loaded
[   11.760343] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   11.923519] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   11.926229] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.961702] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.418356] nvidia: module license 'NVIDIA' taints kernel.
[   12.676892] ACPI: PCI Interrupt Link [AIGP] enabled at IRQ 20
[   12.676898] nvidia 0000:02:00.0: PCI INT A -> Link[AIGP] -> GSI 20 (level, low) -> IRQ 20
[   12.676904] nvidia 0000:02:00.0: setting latency timer to 64
[   12.677031] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  177.80  Wed Oct  1 14:43:46 PDT 2008
[   12.818141] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   12.818153] rt61pci 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   12.825720] phy0: Selected rate control algorithm 'pid'
[   12.896974] Registered led device: rt61pci-phy0:radio
[   12.896989] Registered led device: rt61pci-phy0:assoc
[   13.648721] lp: driver loaded but no devices found
[   13.807324] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k
[   14.368319] EXT3 FS on sda1, internal journal
[   15.618104] type=1505 audit(1228960392.109:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4770
[   15.753884] type=1505 audit(1228960392.245:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4775
[   15.754064] type=1505 audit(1228960392.245:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4775
...

---

### Post by xylene2301 on 2008-12-16
I've experienced similar.  I'm using Heron.  I usually get a bong when the system boots and then sound only on accounts created after I installed the als4000 sound card but sometimes sound on the old accounts.
Nondeterminism...yep.
Which os version are you using?

---

### Post by wmorgan on 2008-12-16
I'm running version 8.10 - Ibix. The problem appears to be unrelated to user accounts: if I don't get a startup sound when the login screen appears, sound will be unavailable after I log in, and if I do get a startup sound, then sound will be available after login.

Maybe it will be helpful if I clarified what I meant by sound not working. When sound doesn't work, aplay -l produces no output. Futhermore lspci -v -s 00:07 (my PCI sound device) includes the line

Kernel driver in use: HDA Intel

when sound is working, but does not contain this line when it isn't.

---

### Post by xylene2301 on 2008-12-17
I'm afraid I'm too new to be helpful.
Just booted my machine and no sound.  It worked fine yesterday.

---

### Post by xylene2301 on 2008-12-17
I'm thinking that it's either some file or driver that doesn't always get loaded or an interrupt that sometimes gets assigned (on the fly?) such that it conflicts.  I guess that covers a lot of territory.

---

### Post by xylene2301 on 2008-12-20
the trick may be to add the driver of your sound card to the 'load modules on startup' list accessed from your terminal by typing  
sudo nano /etc/modules 
     
follow the instructions in the comprehensive sound troublshooting guide here
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Note that the list of alsa drivers is now here:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
It seems to have fixed my problems.

---

### Post by wmorgan on 2008-12-30
The problem was not that the driver module wasn't getting loaded. Even when sound didn't work, the module was loaded on boot. The problem was that my sound card wasn't explicitly supported by the version of ALSA that ships with Ubuntu (1.0.17). However, ALSA was somehow able to correctly configure the options for the driver module some of the time (is there some nondeterminism there?), so I got sound some of the time. My sound card is the nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1) that came with my ASUS motherboard.

The ALC1200 is supported in the newest version of ALSA ( 1.0.18 ). Since upgrading my ALSA, I have gotten sound on 5 out of 5 boots, when before I was getting sound on about 10 out of 30.

Building and installing the latest ALSA was as easy as it gets, but I also found this script, which does the same thing:

[http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695)

---

### Post by stuartmcfadyen on 2009-02-21
Ubuntu 8.10 .... I have searched every forum I can find, installed and followed ALL the hints, tips, etc and still ...... WHEN I BOOT 8.10 I CAN NEVER BE CERTAIN THAT SOUND IS WORKING !
Sometimes, on a random basis, it works other times it does not.
The only cure that guarantees 100% sucess to have sound is to run sudo alsa force-reload. This 8.10 problem is SO STUPID ................ UBUNTU FIX IT !

---

### Post by markbuntu on 2009-02-21
This problem is very common when multiple sound devices are present. Nvidia and ATI include HDMI devices in their gpus now so that means if you have one of them you have multiple sound devices.

What happens is that the devices are on the PCI bus and are detected and assigned somewhat randomly. This means that sometimes your mobo sound chip is detected first and becomes the default and sometimes the HDMI or other device is detected first and becomes the default sound device.

You can fix this

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by stuartmcfadyen on 2009-02-22
Thank you Mark for your technical references which I have read and where necessary installed/amended code. Sorry to say to no avail .... random sound still exists at startup !
My main point though is this ..... it is 2009 ....and having been in IT for over 40 years I thought we had passed the stage of Operating Systems struggling to load the correct drivers etc. 
If Linux is to continue its excellent growth in popularity **(and I want it to)**, it must overcome this type of problem FAST so that newbies are not put off at the first installation hurdle.  
One only has to wonder at the volume of Forum correspondence related to sound problems.
Thanks again for your help, and I shall say no more. 
I will continue to use **[COLOR="Red"]sudo alsa force-reload[/COLOR]** as the solution to my problem.

---

### Post by markbuntu on 2009-02-22
You should check with aplay -l to see the order that the drivers are loaded. If there is a difference between working and non-working you will know what the problem is. You should also look in the logs or run pulseaudio from a terminal with

pulseaudio -vvv

This does not happen to everyone so we need some help from users experiencing it to give us information so the problem can be tracked down and fixed.

---

### Post by stuartmcfadyen on 2009-02-23
Despite my last post saying I would "say no more" I am pleased to report that I HAVE SOLVED MY PROBLEM OF INTERMITTENT SOUND AT BOOT ....... as follows ..... 

(Bear in mind that I only have on-board sound installed on my PC).

1. **Change** all entries in SYSTEM PREFERENCES SOUND to "ALSA - Advanced Linux Sound Architecture"

2. **Edit**  /etc/modprobe.d/alsa-base (lines altered by [COLOR="Red"]**#**[/COLOR] shown in red, as follows)

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
[COLOR="Red"]# install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
# install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
# install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
# install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet # snd-seq-oss ; : ; }
# install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }[/COLOR]
# Cause optional modules to be loaded above sound card driver modules
[COLOR="Red"]# install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-#synth ; }
# install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }[/COLOR]

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
[COLOR="Red"]options snd-hda-intel model=STAC9221 index=-0[/COLOR]

This has given me 10 out of 10 successful boots with sound working OK in Skype, MP3 and DVD players .... Thanks again to all .... maybe this will help others ? :D

---

