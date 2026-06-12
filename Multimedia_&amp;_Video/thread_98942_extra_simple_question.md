---
title: "extra simple question"
date: 2005-12-04
forum: Multimedia &amp; Video
---

### Post by xolot1 on 2005-12-04
im trying to get my sound card working.
ubuntu does not detect it.
i read that i probably need to find the modules, and get them loaded.

can anyone explain quick how this is done, or even just point me to some resources answering this question?

i was using the soundcard HOWTO fix page, but since the card wasnt detected, i hit a wall, and my googling skills arnt coming to fruitation.

---

### Post by nalmeth on 2005-12-04
I am not a sound card wizard, because I've never had any serious sound problems at all, and never had to deal with them. I have had other hardware-to-software related linux problems though.

The best thing to do (if you haven't done already) would be to google search the model name of your sound card with linux or ubuntu. Maybe it is a unique card with no open-drivers. You might need a proprietary driver. This is probably not the case, but it might be. If you can't figure it out by googling, theres nothing better than person to person help.

Post the model name and any other appropriate information here. There are many wizards that come through these forums, and if they have all your info they will undoubtedly give you some help.

Sorry if I'm being redundant here, but obviously all the more details the better.

---

### Post by xolot1 on 2005-12-04
for those of you interested in my hardware:
i have an old computer ~10 years (at least some parts)
733mHz
356 (or so)mb ram
5.10 kubuntu

soundcard (writing everything i know):
creative AWE 4500 - soundblaster AWE65

should use the drivers sb16, or emu8000  (from memory).


anyways, i was hoping to stumble my way through this, and was hoping just for the initial steps to "load the module"

however, if someones at work (or at school like me), and wants to write out a nice guide, im not gonna complain - just dont feel you have to put more than 30 secs in.   ;) thanks

---

### Post by amohanty on 2005-12-04
1. The first step is to see if it was detected via:
```
lspci
```

2. Then check to see if any modules for it are loaded:
```
lsmod
```

3. Then if you have been able to compile and get the .o files for it, look at the ```
insmod
``` program. I havent had to use it at all so far, but if you have to somehow force it in to see if it works thats the way to go. 

4. If you have the rpm you can use  ```
alien
``` to install it and not do (3)
 
5. If everything works add a line to the end of ```
/etc/modules
``` which has the name of the module, (get that using (2)).

HTH
AM

---

### Post by xolot1 on 2005-12-04
thanks for the help!
but...

the card isnt detected.
back under windows it was detected just fine (not that it matters, but at least it i know it worked).

can i copy/paste anything that would help?

---

### Post by schdefan on 2005-12-05
Post all the output from amohanty.
What happens when you execute ```
$alsamixer
```
schdefan

---

### Post by xolot1 on 2005-12-05
```
willi@ubuntu:~$ lspci

```

```
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
0000:00:0f.0 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 26)
0000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400 AGP (rev 04)

```

```
willi@ubuntu:~$ lsmod
Module                  Size  Used by
isofs                  32824  1
udf                    75524  0
nls_utf8                2176  0
nls_cp437               5888  1
vfat                   12288  0
fat                    46492  1 vfat
mga                    56448  1
drm                    58004  2 mga
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
sg                     33696  0
sr_mod                 15652  0
analog                 10528  0
ns558                   5508  0
gameport               14472  3 analog,ns558
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
i2c_piix4               8336  0
i2c_core               19728  2 i2c_acpi_ec,i2c_piix4
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  2 drm,intel_agp
dm_mod                 50364  1
evdev                   9088  0
tsdev                   7616  0
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  4
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
usb_storage            64704  0
3c59x                  37544  0
mii                     5248  1 3c59x
uhci_hcd               28048  0
usbcore               104188  3 usb_storage,uhci_hcd
sd_mod                 17424  4
ide_cd                 36996  1
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  4
ide_generic             1664  0
sym53c8xx              71956  4
scsi_transport_spi     17920  1 sym53c8xx
scsi_mod              124872  6 sg,sr_mod,usb_storage,sd_mod,sym53c8xx,scsi_transport_spi
piix                    9476  1
ide_core              125268  5 usb_storage,ide_cd,ide_disk,ide_generic,piix
unix                   24624  706
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

```

```
willi@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

```

---

### Post by Zimmer on 2005-12-05
Have a look here , the SB 16 awe gets a mention and a parameter...
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

Zimm

---

