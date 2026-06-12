---
title: "Lost sound after changing alsa-base.conf file"
date: 2016-04-04
forum: Multimedia Software
---

### Post by slcooper on 2016-04-04
Dear friends,

I've installed Ubuntu recently on a new notebook (HP 250 G4) and I had a slight problem with sound: it was repeating from time to time, while not going out of sync with video later on. I tried to help alsa by adding 

```

options snd-hda-intel model=generic
```

to 

```
/etc/modprobe.d/alsa-base.conf
```

After a reboot, sound was off: instead of built-in speakers I got dummy output in the mixer. So I changed the line to model = auto to see if it is going to work then, but it didn't.

In efforts to fix it, I purged alsa and pulseaudio, got them again, forced alsa, reverted my kernel, but nothing really happened. I still have the dummy output and 

Here's my AlsaInfo:

[http://www.alsa-project.org/db/?f=2dcdbebbc999cd00f7e0f2e6a69fae2843e5a2aa](http://www.alsa-project.org/db/?f=2dcdbebbc999cd00f7e0f2e6a69fae2843e5a2aa)

```
!!################################
!!ALSA Information Script v 0.4.64
!!################################

!!Script ran on: Mon Apr  4 04:28:13 UTC 2016


!!Linux Distribution
!!------------------

Ubuntu 15.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 15.10" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 15.10" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      HP
Product Name:      HP 250 G4 Notebook PC
Product Version:   Type1ProductConfigId
Firmware Version:  F.1B


!!Kernel Information
!!------------------

Kernel release:    4.2.0-34-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k4.2.0-34-generic
Library version:    1.0.29
Utilities version:  1.0.29


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1f.3 Audio device: Intel Corporation Device 9d70 (rev 21)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:1f.3 0403: 8086:9d70 (rev 21)
    Subsystem: 103c:8136


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

crw-rw----  1 root audio 116,  1 Apr  4 04:24 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Apr  4 04:24 /dev/snd/timer


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
rfcomm
drbg
ansi_cprng
ctr
ccm
bnep
nls_iso8859_1
snd_hda_intel
snd_hda_codec
snd_hda_core
snd_hwdep
snd_pcm
hp_wmi
snd_seq_midi
sparse_keymap
snd_seq_midi_event
joydev
intel_rapl
snd_rawmidi
x86_pkg_temp_thermal
intel_powerclamp
coretemp
kvm
arc4
crct10dif_pclmul
crc32_pclmul
snd_seq
rtl8723be
btcoexist
rtl8723_common
rtl_pci
rtlwifi
mac80211
aesni_intel
aes_x86_64
lrw
gf128mul
snd_seq_device
glue_helper
snd_timer
ablk_helper
cryptd
snd
input_leds
serio_raw
cfg80211
soundcore
shpchp
btusb
btrtl
btbcm
btintel
bluetooth
processor_thermal_device
int340x_thermal_zone
mei_me
mei
intel_soc_dts_iosf
intel_lpss_acpi
intel_lpss
int3400_thermal
hp_wireless
tpm_crb
acpi_thermal_rel
acpi_pad
mac_hid
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
v4l2_common
videodev
media
parport_pc
ppdev
lp
parport
autofs4
i915
psmouse
i2c_algo_bit
drm_kms_helper
drm
r8169
ahci
mii
libahci
wmi
i2c_hid
video
pinctrl_sunrisepoint
hid
pinctrl_intel


!!ALSA/HDA dmesg
!!--------------

[    2.144458] rtl8723be 0000:03:00.0 wlp3s0: renamed from wlan0
[    2.165934] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    2.168386] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7651 MBytes.
--
[    2.180384] Adding 8284156k swap on /dev/sda3.  Priority:-1 extents:1 across:8284156k SSFS
[    2.283705] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[    2.285256] snd_hda_intel 0000:00:1f.3: no codecs found!
[    2.320300] audit: type=1400 audit(1459743863.495:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=527 comm="apparmor_parser"



```

Update: I started the system in upstart mode and sound runs normally. Still, I want to run it "normally" so I'm still looking for an answer here.

---

