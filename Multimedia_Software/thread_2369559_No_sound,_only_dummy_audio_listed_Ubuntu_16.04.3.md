---
title: "No sound, only dummy audio listed Ubuntu 16.04.3"
date: 2017-08-24
forum: Multimedia Software
---

### Post by xprienzo on 2017-08-24
Recently something happened with my PC while trying to install official realtek drivers and it started showing no sound at all. After trying to undo stuff I did before and reinstalling pulse audio, now there's only a dummy audio option in the audio controls, with no soundcards listed in $aplay -l

Output of ```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
```
is [here]("http://www.alsa-project.org/db/?f=ff2e67a338cfe2633e3ff3a5d2d7e2485c503a07")
```

!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Thu Aug 24 12:42:44 UTC 2017


!!Linux Distribution
!!------------------

Ubuntu 16.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial


!!DMI Information
!!---------------

Manufacturer:      Hewlett-Packard
Product Name:      HP 15 Notebook PC
Product Version:   0991100000000000000600087
Firmware Version:  F.39
Board Vendor:      Hewlett-Packard
Board Name:        2212


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/111D4D07:00/status      15
/sys/bus/acpi/devices/BCM2E49:00/status      15
/sys/bus/acpi/devices/EETI7900:00/status      15
/sys/bus/acpi/devices/INT340E:00/status      15
/sys/bus/acpi/devices/INT3F0D:00/status      15
/sys/bus/acpi/devices/LNXVIDEO:00/status      15
/sys/bus/acpi/devices/MSFT0001:00/status      15
/sys/bus/acpi/devices/PNP0103:00/status      11
/sys/bus/acpi/devices/PNP0C0A:00/status      31
/sys/bus/acpi/devices/PNP0C0B:00/status      15
/sys/bus/acpi/devices/PNP0C0D:00/status      15
/sys/bus/acpi/devices/PNP0C0F:00/status      9
/sys/bus/acpi/devices/PNP0C0F:01/status      9
/sys/bus/acpi/devices/PNP0C0F:02/status      9
/sys/bus/acpi/devices/PNP0C0F:03/status      9
/sys/bus/acpi/devices/PNP0C0F:04/status      9
/sys/bus/acpi/devices/PNP0C0F:05/status      9
/sys/bus/acpi/devices/PNP0C0F:06/status      9
/sys/bus/acpi/devices/PNP0C0F:07/status      9
/sys/bus/acpi/devices/SYN1EAE:00/status      15
/sys/bus/acpi/devices/device:18/status      15
/sys/bus/acpi/devices/device:19/status      15
/sys/bus/acpi/devices/device:1a/status      15
/sys/bus/acpi/devices/device:1b/status      15
/sys/bus/acpi/devices/device:1c/status      15
/sys/bus/acpi/devices/device:1e/status      15
/sys/bus/acpi/devices/device:1f/status      15
/sys/bus/acpi/devices/device:20/status      15
/sys/bus/acpi/devices/device:21/status      15
/sys/bus/acpi/devices/device:28/status      15
/sys/bus/acpi/devices/device:29/status      15
/sys/bus/acpi/devices/device:2a/status      15
/sys/bus/acpi/devices/device:2b/status      15
/sys/bus/acpi/devices/device:2f/status      15
/sys/bus/acpi/devices/device:32/status      15
/sys/bus/acpi/devices/device:34/status      15
/sys/bus/acpi/devices/device:43/status      15
/sys/bus/acpi/devices/device:50/status      15


!!Kernel Information
!!------------------

Kernel release:    4.4.0-92-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.1.0
Utilities version:  1.1.0


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------



!!PCI Soundcards installed in the system
!!--------------------------------------

00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:03.0 0403: 8086:0a0c (rev 0b)
    Subsystem: 103c:2212
--
00:1b.0 0403: 8086:9c20 (rev 04)
    Subsystem: 103c:2212


!!Modprobe options (Sound related)
!!--------------------------------

snd_pcsp: index=-2
snd_usb_audio: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_atiixp_modem: index=-2
snd_intel8x0m: index=-2
snd_via82xx_modem: index=-2
snd_usb_audio: index=-2
snd_usb_caiaq: index=-2
snd_usb_ua101: index=-2
snd_usb_us122l: index=-2
snd_usb_usx2y: index=-2
snd_cmipci: mpu_port=0x330 fm_port=0x388
snd_pcsp: index=-2
snd_usb_audio: index=-2


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Aug 24 11:22 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Aug 24 11:22 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:268: no soundcards found...

ARECORD

arecord: device_list:268: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
drbg
ansi_cprng
ctr
ccm
bbswitch
nvidia_uvm
arc4
rt2800pci
intel_rapl
rt2800mmio
x86_pkg_temp_thermal
intel_powerclamp
rt2800lib
coretemp
rt2x00pci
rt2x00mmio
rt2x00lib
mac80211
kvm
nvidia
cfg80211
irqbypass
uvcvideo
videobuf2_vmalloc
videobuf2_memops
crct10dif_pclmul
videobuf2_v4l2
crc32_pclmul
ghash_clmulni_intel
videobuf2_core
v4l2_common
videodev
rtsx_pci_ms
eeprom_93cx6
crc_ccitt
media
memstick
aesni_intel
aes_x86_64
lrw
gf128mul
glue_helper
i2c_designware_platform
ablk_helper
i2c_designware_core
cryptd
input_leds
8250_dw
joydev
serio_raw
snd_soc_sst_acpi
lpc_ich
dw_dmac
spi_pxa2xx_platform
dw_dmac_core
shpchp
mei_me
mei
soc_button_array
intel_hid
mac_hid
hp_wmi
sparse_keymap
wmi
parport_pc
ppdev
lp
parport
autofs4
hid_generic
usbhid
rtsx_pci_sdmmc
i915
i2c_algo_bit
drm_kms_helper
syscopyarea
sysfillrect
psmouse
sysimgblt
fb_sys_fops
ahci
drm
libahci
r8169
rtsx_pci
mii
i2c_hid
sdhci_acpi
hid
video
sdhci
fjes


!!ALSA/HDA dmesg
!!--------------
 
```


Can someone please help me recover the sound?

---

### Post by steevi93 on 2017-08-24
Hi there:

I had a very similar issue that I resolved this morning.

I installed pavucontrol, ran the program, scrolled the top menu all the way to the left for "Configuration" and changed the profile.  Mine started working on Analogue Stereo Duplex.

---

### Post by xprienzo on 2017-08-24
[IMG]http://i.imgur.com/eYUNMFf.png[/IMG]
This is what shows up in there.

---

### Post by xprienzo on 2017-08-24
running ```
sudo modprobe snd_hda_intel
``` worked. I guess will have to set it up to run on system boot.

---

