---
title: "Lost sound after reboot - sound card not detected"
date: 2020-07-21
forum: Multimedia Software
---

### Post by gibagiba on 2020-07-21
Hey guys,

Got an issue with sound after I rebooted my PC (to be precise, I logged out first, then logged back in and noticed that there is no sound. I checked pavucontrol and everything seemed fine there, so I hoped a reboot would solve the issue). 

After rebooting I noticed that pavucontrol doesn't show any devices anymore and just shows 'Dummy Output'. So, basucally, my sound card is not detected by ALSA:

```

$ aplay -l
aplay: device_list:268: no soundcards found...

```

However, hardware is recognized:
```

$ lspci | grep -i audio
00:1f.3 Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)

```

What I've tried so far:
[LIST]
[*]all the different ways of upgrading/reinstalling/restarting alsa/pulseaudio
[*]removing ~/.config/pulse and similar ways of clearing the cache
[*]installing latest alsa driver using this link [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)
[*]step1/step3 from sound troubleshooting guide [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
[*]playing with a probe_mask (just tried some suggestions from the forums, don't really know what I'm doing here)
[/LIST]

Below is some info that might help understanding my issue:

```

!!################################
!!ALSA Information Script v 0.4.65
!!################################


!!Script ran on: Tue Jul 21 15:43:08 UTC 2020




!!Linux Distribution
!!------------------


Ubuntu 16.04.6 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 16.04.6 LTS" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 16.04.6 LTS" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/" UBUNTU_CODENAME=xenial




!!DMI Information
!!---------------


Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      Z170-HD3
Product Version:   Default string
Firmware Version:  F20
Board Vendor:      Gigabyte Technology Co., Ltd.
Board Name:        Z170-HD3-CF




!!ACPI Device Status Information
!!---------------


/sys/bus/acpi/devices/ACPI000C:00/status      15
/sys/bus/acpi/devices/INT33A1:00/status      15
/sys/bus/acpi/devices/INT340E:00/status      15
/sys/bus/acpi/devices/INT3F0D:00/status      15
/sys/bus/acpi/devices/LNXPOWER:00/status      1
/sys/bus/acpi/devices/LNXPOWER:01/status      1
/sys/bus/acpi/devices/LNXPOWER:02/status      1
/sys/bus/acpi/devices/LNXPOWER:03/status      1
/sys/bus/acpi/devices/LNXPOWER:04/status      1
/sys/bus/acpi/devices/LNXPOWER:05/status      1
/sys/bus/acpi/devices/LNXPOWER:06/status      1
/sys/bus/acpi/devices/LNXPOWER:07/status      1
/sys/bus/acpi/devices/LNXPOWER:08/status      1
/sys/bus/acpi/devices/LNXPOWER:09/status      1
/sys/bus/acpi/devices/LNXPOWER:0a/status      1
/sys/bus/acpi/devices/LNXPOWER:0b/status      1
/sys/bus/acpi/devices/LNXPOWER:0c/status      1
/sys/bus/acpi/devices/LNXPOWER:0d/status      1
/sys/bus/acpi/devices/LNXPOWER:0e/status      1
/sys/bus/acpi/devices/LNXPOWER:0f/status      1
/sys/bus/acpi/devices/LNXPOWER:10/status      1
/sys/bus/acpi/devices/LNXPOWER:11/status      1
/sys/bus/acpi/devices/LNXPOWER:12/status      1
/sys/bus/acpi/devices/LNXPOWER:13/status      1
/sys/bus/acpi/devices/LNXPOWER:14/status      1
/sys/bus/acpi/devices/LNXPOWER:15/status      1
/sys/bus/acpi/devices/LNXPOWER:16/status      1
/sys/bus/acpi/devices/PNP0103:00/status      15
/sys/bus/acpi/devices/PNP0400:00/status      15
/sys/bus/acpi/devices/PNP0501:00/status      15
/sys/bus/acpi/devices/PNP0C02:02/status      15
/sys/bus/acpi/devices/PNP0C02:04/status      3
/sys/bus/acpi/devices/PNP0C02:06/status      3
/sys/bus/acpi/devices/PNP0C04:00/status      31
/sys/bus/acpi/devices/PNP0C0C:00/status      15
/sys/bus/acpi/devices/PNP0C0E:00/status      11
/sys/bus/acpi/devices/PNP0C0F:00/status      9
/sys/bus/acpi/devices/PNP0C0F:01/status      9
/sys/bus/acpi/devices/PNP0C0F:02/status      9
/sys/bus/acpi/devices/PNP0C0F:03/status      9
/sys/bus/acpi/devices/PNP0C0F:04/status      9
/sys/bus/acpi/devices/PNP0C0F:05/status      9
/sys/bus/acpi/devices/PNP0C0F:06/status      9
/sys/bus/acpi/devices/PNP0C0F:07/status      9
/sys/bus/acpi/devices/device:69/status      15
/sys/bus/acpi/devices/device:75/status      11




!!Kernel Information
!!------------------


Kernel release:    4.4.0-151-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes




!!ALSA Version
!!------------


Driver version:     k4.4.0-151-generic
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


--- no soundcards ---




!!PCI Soundcards installed in the system
!!--------------------------------------


00:1f.3 Audio device [0403]: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller [8086:a170] (rev 31)
    Subsystem: Gigabyte Technology Co., Ltd Sunrise Point-H HD Audio [1458:a182]




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


crw-rw----+ 1 root audio 116,  1 Jul 21 17:42 /dev/snd/seq
crw-rw----+ 1 root audio 116, 33 Jul 21 17:42 /dev/snd/timer




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


8250_fintek
ablk_helper
acpi_pad
aes_x86_64
aesni_intel
ahci
aufs
autofs4
binfmt_misc
br_netfilter
bridge
coretemp
crc32_pclmul
crct10dif_pclmul
cryptd
drm
drm_kms_helper
fb_sys_fops
fjes
gf128mul
ghash_clmulni_intel
glue_helper
hid
hid_generic
i2c_algo_bit
i915_bpo
input_leds
intel_ips
intel_powerclamp
intel_rapl
ip6_tables
ip6table_filter
ip_tables
ipt_MASQUERADE
iptable_filter
iptable_nat
irqbypass
joydev
kvm
kvm_intel
libahci
llc
lp
lrw
mac_hid
mei
mei_me
mii
nf_conntrack
nf_conntrack_ipv4
nf_defrag_ipv4
nf_nat
nf_nat_ipv4
nf_nat_masquerade_ipv4
parport
parport_pc
pci_stub
ppdev
psmouse
r8169
serio_raw
shpchp
snd
snd_hda_codec
snd_hda_core
snd_hda_intel
snd_hwdep
snd_pcm
snd_rawmidi
snd_seq
snd_seq_device
snd_seq_midi
snd_seq_midi_event
snd_timer
soundcore
stp
syscopyarea
sysfillrect
sysimgblt
usbhid
vboxdrv
vboxnetadp
vboxnetflt
vboxpci
video
wmi
x86_pkg_temp_thermal
x_tables
xfrm_algo
xfrm_user
xt_addrtype
xt_conntrack
xt_tcpudp




!!ALSA/HDA dmesg
!!--------------


[   26.400486] audit: type=1400 audit(1595342541.177:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="docker-default" pid=486 comm="apparmor_parser"
[   27.283403] snd_hda_core: loading out-of-tree module taints kernel.
[   27.283436] snd_hda_core: module verification failed: signature and/or required key missing - tainting kernel
[   27.356930] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.1
[   27.357038] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[   27.466500] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[   27.468010] snd_hda_intel 0000:00:1f.3: no codecs found!
[   27.674740] audit: type=1400 audit(1595342542.449:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=548 comm="apparmor_parser"
--
[   98.834352] aufs au_opts_verify:1597:dockerd[1557]: dirperm1 breaks the protection by the permission bits on the lower branch
[  406.798605] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.1
[  406.798730] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[  406.910012] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[  406.911590] snd_hda_intel 0000:00:1f.3: no codecs found!
[ 1199.010806] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.1
[ 1199.010896] snd_hda_intel 0000:00:1f.3: codec_mask forced to 0xff
[ 1199.010924] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[ 1199.120563] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[ 1199.122140] snd_hda_intel 0000:00:1f.3: no codecs found!




!!Packages installed
!!--------------------


ii  alsa-oss                                        1.0.28-1ubuntu1                               amd64        ALSA wrapper for OSS applications
ii  alsa-tools                                      1.1.0-0ubuntu1                                amd64        Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                  1.1.0-0ubuntu1                                amd64        GUI based ALSA utilities for specific hardware
ii  alsa-utils                                      1.1.0-0ubuntu5                                amd64        Utilities for configuring and using ALSA


```

```

$ lsmod | grep snd
snd_hda_intel          40960  0
snd_hda_codec         139264  1 snd_hda_intel
snd_hda_core           94208  2 snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
snd_pcm               106496  3 snd_hda_codec,snd_hda_intel,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    86016  8 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  1 snd

```

```

$ ls -l /etc/modprobe.d/
total 68K
-rw-r--r-- 1 root root 2.5K Jul 21 18:58 alsa-base.conf
-rw-r--r-- 1 root root  154 Jul  2  2018 amd64-microcode-blacklist.conf
-rwxrwxrwx 1 root root  325 Apr 18  2013 blacklist-ath_pci.conf*
-rwxrwxrwx 1 root root 1.7K Nov 13  2018 blacklist.conf*
-rwxrwxrwx 1 root root  210 Apr 18  2013 blacklist-firewire.conf*
-rwxrwxrwx 1 root root  697 Mar 13  2016 blacklist-framebuffer.conf*
-rw-r--r-- 1 root root  156 Jul 31  2015 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Jul 21 16:59 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rwxrwxrwx 1 root root  583 Apr 18  2013 blacklist-rare-network.conf*
-rwxrwxrwx 1 root root 1.1K Apr 18  2013 blacklist-watchdog.conf*
-rwxrwxrwx 1 root root  127 Oct 31  2012 dkms.conf*
-rwxrwxrwx 1 root root  390 Jan 12  2017 fbdev-blacklist.conf*
-rw-r--r-- 1 root root  154 Nov 10  2015 intel-microcode-blacklist.conf
-rwxrwxrwx 1 root root  347 Apr 18  2013 iwlwifi.conf*
-rw-r--r-- 1 root root   16 Mar  8  2009 libpisock9.conf
-rwxrwxrwx 1 root root  104 Apr 18  2013 mlx4.conf*
-rw-r--r-- 1 root root  153 Feb 15  2017 nvidia-378_hybrid.conf
-rwxrwxrwx 1 root root   30 Aug  2  2012 vmwgfx-fbdev.conf*

```


This part seems the most troubling for me:

```

$ dmesg | grep hda
[   27.283403] snd_hda_core: loading out-of-tree module taints kernel.
[   27.283436] snd_hda_core: module verification failed: signature and/or required key missing - tainting kernel
[   27.356930] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.1
[   27.357038] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[   27.466500] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[   27.468010] snd_hda_intel 0000:00:1f.3: no codecs found!
[  406.798605] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.1
[  406.798730] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[  406.910012] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[  406.911590] snd_hda_intel 0000:00:1f.3: no codecs found!
[ 1199.010806] snd_hda_intel 0000:00:1f.3: Probing card using HDA DKMS, version 0.1
[ 1199.010896] snd_hda_intel 0000:00:1f.3: codec_mask forced to 0xff
[ 1199.010924] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915_bpo])
[ 1199.120563] snd_hda_intel 0000:00:1f.3: CORB reset timeout#1, CORBRP = 0
[ 1199.122140] snd_hda_intel 0000:00:1f.3: no codecs found!

```

Not sure why the codecs can't be found. It is possible that I might be missing something obvious. It seems strange that just a reboot would cause something like this. I don't think I made any modifications before rebooting which could cause an issue like this. 

Any advices would be helpful. Thank you very much in advance!

---

### Post by claus on 2020-07-23
Hi,

are you still using Ubuntu 16.04.6 LTS? What desktop environment? Have you considered upgrading to 20.04 LTS? I'm using Ubuntu MATE 20.04, which I like much better than Unity.

Claus

---

### Post by Yellow Pasque on 2020-07-25
Try disabling audio codec in the BIOS/EFI. Then reboot and reenable it.

---

