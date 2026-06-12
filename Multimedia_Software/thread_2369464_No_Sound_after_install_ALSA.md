---
title: "No Sound after install ALSA"
date: 2017-08-23
forum: Multimedia Software
---

### Post by steevi93 on 2017-08-23
Hi:

I am a relative noob to Ubuntu (been working in Windows for years) but working in a role that is built around Linux, I've dipped my toe into the pond, so to speak, and fallen in love with it.

I have a Toshiba Satellite C50-B-14D laptop dual boot laptop with Ubuntu 16.04 O/S and Windows 10.  It also has a shared mic/headphone port (1 port, dual I/O).  In Windows, it works fine.  In Ubuntu, it works headphone only, but no mic input, which I need for my side project as an internet radio DJ.

I install (or so I thought) the relevant drivers from Realtek for Linux to the device (found here:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)) and installed.  However, it seems to have failed, and now I have no sound at all.  

I ran 
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

to try and revert the changes, but still no go.  Any advice?

---

### Post by steevi93 on 2017-08-23
I don't know if this helps, but I ran 
wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh 

and got the below output:

```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Wed Aug 23 11:31:17 UTC 2017


!!Linux Distribution
!!------------------

Ubuntu 16.04.3 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04.3 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04.3 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      SATELLITE C50-B
Product Version:   PSCMLE-02N025EN
Firmware Version:  1.70
Board Vendor:      TOSHIBA
Board Name:        ZBWAA


!!ACPI Device Status Information
!!---------------

/sys/bus/acpi/devices/ATML2000:00/status 	 15
/sys/bus/acpi/devices/BCM2E1A:00/status 	 15
/sys/bus/acpi/devices/INT3396:00/status 	 15
/sys/bus/acpi/devices/INTCF0B:00/status 	 15
/sys/bus/acpi/devices/INTCF1A:00/status 	 15
/sys/bus/acpi/devices/INTCF1C:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:00/status 	 15
/sys/bus/acpi/devices/LNXPOWER:01/status 	 1
/sys/bus/acpi/devices/LNXPOWER:02/status 	 1
/sys/bus/acpi/devices/LNXPOWER:03/status 	 1
/sys/bus/acpi/devices/LNXPOWER:04/status 	 1
/sys/bus/acpi/devices/LNXPOWER:05/status 	 1
/sys/bus/acpi/devices/PNP0103:00/status 	 15
/sys/bus/acpi/devices/PNP0C0A:03/status 	 31
/sys/bus/acpi/devices/PNP0C0F:00/status 	 9
/sys/bus/acpi/devices/PNP0C0F:01/status 	 9
/sys/bus/acpi/devices/PNP0C0F:02/status 	 9
/sys/bus/acpi/devices/PNP0C0F:03/status 	 9
/sys/bus/acpi/devices/PNP0C0F:04/status 	 9
/sys/bus/acpi/devices/PNP0C0F:05/status 	 9
/sys/bus/acpi/devices/PNP0C0F:06/status 	 9
/sys/bus/acpi/devices/PNP0C0F:07/status 	 9
/sys/bus/acpi/devices/SMO91D0:00/status 	 15
/sys/bus/acpi/devices/TOS0330:00/status 	 15
/sys/bus/acpi/devices/TOS1106:00/status 	 15
/sys/bus/acpi/devices/TOS1900:00/status 	 11
/sys/bus/acpi/devices/TOS6205:00/status 	 15
/sys/bus/acpi/devices/device:0e/status 	 15
/sys/bus/acpi/devices/device:0f/status 	 15
/sys/bus/acpi/devices/device:24/status 	 15
/sys/bus/acpi/devices/device:50/status 	 15
/sys/bus/acpi/devices/device:54/status 	 15


!!Kernel Information
!!------------------

Kernel release:    4.8.0-52-generic
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

00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:0f04 (rev 0e)
	Subsystem: 1179:f91b


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

crw-rw----  1 root audio 116,  1 Aug 23 12:16 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Aug 23 12:16 /dev/snd/timer


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
ccm
rfcomm
bnep
binfmt_misc
ath3k
btusb
btrtl
uvcvideo
intel_rapl
arc4
intel_soc_dts_iosf
intel_powerclamp
coretemp
videobuf2_vmalloc
videobuf2_memops
videobuf2_v4l2
videobuf2_core
videodev
kvm_intel
ath9k
kvm
media
irqbypass
ath9k_common
ath9k_hw
ath
mac80211
punit_atom_debug
cfg80211
crct10dif_pclmul
rtsx_pci_ms
crc32_pclmul
ghash_clmulni_intel
memstick
cryptd
intel_cstate
hci_uart
btbcm
btqca
toshiba_acpi
shpchp
btintel
mei_txe
input_leds
sparse_keymap
bluetooth
mei
industrialio
joydev
wmi
serio_raw
lpc_ich
toshiba_haps
toshiba_bluetooth
rfkill_gpio
i2c_designware_platform
dw_dmac
dw_dmac_core
i2c_designware_core
8250_dw
mac_hid
spi_pxa2xx_platform
pwm_lpss_platform
pwm_lpss
parport_pc
ppdev
lp
parport
autofs4
rtsx_pci_sdmmc
psmouse
rtsx_pci
r8169
mii
ahci
libahci
i915
i2c_algo_bit
drm_kms_helper
syscopyarea
sysfillrect
sysimgblt
fb_sys_fops
drm
video
fjes
i2c_hid
hid
sdhci_acpi
sdhci


!!ALSA/HDA dmesg
!!--------------
```

---

### Post by marseille2 on 2017-08-24
Pulseaudio is on and running but it thinks you have no recognized soundcard by ALSA. At the same time, the system knows you have an Intel CPU with a "High Definition Audio Controller."  If you had sound before, it might not be a problem with ALSA but pulseaudio. Take a look at what's happening at the command line with:

```
$ pacmd list-sinks
```

It will tell you whether or not it's recognizing ALSA sinks (see more about pacmd: [here]("https://askubuntu.com/questions/71863/how-to-change-pulseaudio-sink-with-pacmd-set-default-sink-during-playback"), [here]("https://wiki.archlinux.org/index.php/PulseAudio/Examples#Set_default_input_sources"), and [here]("https://linux.die.net/man/1/pacmd")). 

Also... you might want to install [pasystray]("http://manpages.ubuntu.com/manpages/xenial/man1/pasystray.1.html") to choose your mic input or switch soundcards on the fly. (It lists audio cards as "sinks" and mics as "source").

---

### Post by steevi93 on 2017-08-24
I have managed to fix it.  I installed pavucontrol and played around with the built-in audio controller.  Switched profile to Analogue Stereo Duplex and BOOM....  sound!

---

