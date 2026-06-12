---
title: "Sound not working. Card not recognized."
date: 2014-12-18
forum: Multimedia Software
---

### Post by javiert on 2014-12-18
Hi

After spending the whole day reading in forums, I give up, I can not find the solution. I am not an expert in Linux but I don't know what else to try.

I have ubuntu 14.04 LTS in my Toshiba Portege Z830. When I installed ubuntu everything was working. Then today I installed Lightworks and KDenLive to make some video edition. I tried both, but only adding videos. Later, I created a new video exporting my project with Lightworks and after that the issues came. My sound wasn't working anymore. I uninstall Lightworks using the Ubuntu software center. 

I uninstall alsa and pulse so many times and never work. Even though, what happen when I do that is that my System settings disappear and I have to install them again. 

I DO NOT want to install ubuntu from scratch again. I reinstall the kernel:
ii  linux-image-3.13.0-43-generic       3.13.0-43.72     amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
with: 
sudo apt-get install --reinstall linux-image-3.X.Y-ZZ-generic

```
 sudo lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 6 Series/C200 Series Chipset Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c0720000-c0723fff
```

```
lspci | grep "Audio"
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)

```

Not results as user, sudo...
```
$: aplay -l
aplay: device_list:268: no soundcards found...

```

Alsamixer is not working either. Even with the alsa-utils and tools installed. "cannot open mixer: No such file or directory"

I am having similar issues to this topic but I can not solve it and I don't get anything if I run "sudo aplay -l" 
[URL="http://ubuntuforums.org/showthread.php?t=2166214"]http://ubuntuforums.org/showthread.php?t=2166214
[/URL]
I have tried this too but I always have the Dummy Output
[http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/](http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/)

```
sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).

```

> ```
$: bash alsa-info.sh --stdout
cat: /proc/asound/version: No such file or directory
grep: /proc/asound/cards: No such file or directory
cat: /proc/asound/cards: No such file or directory
cat: /proc/asound/modules: No such file or directory
grep: /proc/asound/cards: No such file or directory
/usr/sbin/alsactl: save_state:1590: No soundcards found...
cat: /tmp/alsa-info.DwBVaLwFpi/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Thu Dec 18 23:07:09 UTC 2014


!!Linux Distribution
!!------------------

Ubuntu 14.04.1 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 14.04.1 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      TOSHIBA
Product Name:      PORTEGE Z830
Product Version:   PT224E-00G00JCE
Firmware Version:  Version 1.80  


!!Kernel Information
!!------------------

Kernel release:    3.13.0-43-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     
Library version:    1.0.27.2
Utilities version:  1.0.27.2


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

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1b.0 0403: 8086:1c20 (rev 04)
    Subsystem: 1179:0001


!!Modprobe options (Sound related)
!!--------------------------------

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
snd_hda_intel: index=0
snd_usb_audio: index=1
snd_usb_audio: index=2
snd_hda_intel: model=auto


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116,  1 Dec 18 23:34 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Dec 18 23:34 /dev/snd/timer


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
ctr
ccm
ath3k
btusb
bnep
rfcomm
bluetooth
arc4
intel_rapl
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
ath9k
x86_pkg_temp_thermal
videodev
intel_powerclamp
hid_generic
coretemp
kvm_intel
ath9k_common
ath9k_hw
kvm
crct10dif_pclmul
ath
crc32_pclmul
ghash_clmulni_intel
usbhid
aesni_intel
hid
mac80211
aes_x86_64
lrw
gf128mul
glue_helper
ablk_helper
cryptd
i915
cfg80211
toshiba_acpi
drm_kms_helper
sparse_keymap
toshiba_bluetooth
wmi
joydev
drm
mei_me
i2c_algo_bit
mei
video
mac_hid
lpc_ich
serio_raw
binfmt_misc
parport_pc
ppdev
lp
parport
psmouse
ahci
e1000e
libahci
sdhci_pci
ptp
sdhci
pps_core


!!ALSA/HDA dmesg
!!--------------



```

I attach the alsa.conf file
[ATTACH]258674[/ATTACH]

Thank you in advance. I hope you can help me.

---

### Post by Yellow Pasque on 2014-12-19
What happens when you try to manually load the module?
```
sudo modprobe -v snd-hda-intel
```

You also may want to try reinstalling (latest) driver/module: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by javiert on 2014-12-19
```
$: sudo modprobe -v snd-hda-intel
modprobe: FATAL: Module snd-hda-intel not found.
```

I tried the second and here is the output i got

> ```
 $: sudo dpkg -i oem-audio-hda-daily-dkms_0.201412181801~ubuntu14.04.1_all.deb 
Selecting previously unselected package oem-audio-hda-daily-dkms.
(Reading database ... 294519 files and directories currently installed.)
Preparing to unpack oem-audio-hda-daily-dkms_0.201412181801~ubuntu14.04.1_all.deb ...
Unpacking oem-audio-hda-daily-dkms (0.201412181801~ubuntu14.04.1) ...
Setting up oem-audio-hda-daily-dkms (0.201412181801~ubuntu14.04.1) ...
Loading new oem-audio-hda-daily-0.201412181801~ubuntu14.04.1 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-43-generic
Building for architecture x86_64
Building initial module for 3.13.0-43-generic
Done.

snd-hda-codec-ca0132:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-cmedia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-controller.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-cirrus.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-ca0110.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-hdmi.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-analog.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-generic.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-idt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-realtek.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-via.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-intel.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-conexant.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

snd-hda-codec-si3054.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-43-generic/updates/dkms/

depmod....

DKMS: install completed.


```

And working!! You saved my life!

Last time, I tried with the step 3 on [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure), but I got an error with the repository, this time I download the package from that website and it worked perfectly. 

Thank you very much

---

