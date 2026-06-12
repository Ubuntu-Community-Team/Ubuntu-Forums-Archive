---
title: "Onboard NIC not detected"
date: 2005-12-11
forum: Networking &amp; Wireless
---

### Post by kook44 on 2005-12-11
Hi-
I have a dell deimension 9150 w/ onboard LAN.  In the windows device manager, the adapter is listed as Intel(R) PRO/1000 PL.
It is not detected by ubuntu.  I have dobe extensive searching online, and haven't found much.  The only thing I found was instructions to add the module to the kernel by typing "modprobe e1000".  I have done so, and there are no noticeable results.  When I type "ifconfig", only the loopback is listed.  If I try "ifup eth0" or "ifconfig eth0"  I recieve error messages saying the device does not exist.

This is the output of lspci:
```

0000:00:00.0 Host bridge: Intel Corp.: Unknown device 2770
0000:00:01.0 PCI bridge: Intel Corp.: Unknown device 2771
0000:00:1b.0 0403: Intel Corp.: Unknown device 27d8 (rev 01)
0000:00:1c.0 PCI bridge: Intel Corp.: Unknown device 27d0 (rev 01)
0000:00:1c.4 PCI bridge: Intel Corp.: Unknown device 27e0 (rev 01)
0000:00:1c.5 PCI bridge: Intel Corp.: Unknown device 27e2 (rev 01)
0000:00:1d.0 USB Controller: Intel Corp.: Unknown device 27c8 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp.: Unknown device 27c9 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp.: Unknown device 27ca (rev 01)
0000:00:1d.3 USB Controller: Intel Corp.: Unknown device 27cb (rev 01)
0000:00:1d.7 USB Controller: Intel Corp.: Unknown device 27cc (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corp.: Unknown device 27b0 (rev 01)
0000:00:1f.1 IDE interface: Intel Corp.: Unknown device 27df (rev 01)
0000:00:1f.2 0106: Intel Corp.: Unknown device 27c1 (rev 01)
0000:00:1f.3 SMBus: Intel Corp.: Unknown device 27da (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5b60
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5b70
0000:04:00.0 Ethernet controller: Intel Corp.: Unknown device 109a (rev 01)
0000:05:02.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology Inc) PCI0680 Ultra ATA-133 Host Controller (rev 02)
0000:05:04.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)


```
why are there so many "Unknown Diveces"  (including the Ethernet controller...)
and lsmod:
```

Module                  Size  Used by
e100                   32768  0
mii                     5248  1 e100
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
ipv6                  217408  6
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
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
tsdev                   7616  0
rtc                    11832  0
pcspkr                  3652  0
ohci1394               30644  0
hw_random               5268  0
snd_hda_intel          15872  3
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
sd_mod                 17424  3
ide_disk               16128  3
usb_storage            64704  2
usbhid                 30688  0
siimage                11392  1
ahci                   11268  3
libata                 47876  1 ahci
scsi_mod              124872  6 sr_mod,sbp2,sd_mod,usb_storage,ahci,libata
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0
piix                    9476  1
ide_core              125268  6 ide_disk,usb_storage,siimage,ide_cd,ide_generic,piix
unix                   24624  642
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
I would appreciate any help - this is very frustrating!  :confused:

---

### Post by mips on 2006-02-16
[http://www.ubuntuforums.org/showthread.php?p=741687](http://www.ubuntuforums.org/showthread.php?p=741687)

Thanks to ubuntulifestyle for the french to english tranlation of the wiki page.

---

