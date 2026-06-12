---
title: "No audio devices - Kubuntu 13.04"
date: 2013-07-01
forum: Multimedia Software
---

### Post by slooksterpsv on 2013-07-01
So it's not detecting my audio in Kubuntu 13.04, here's my stats:

```

shawn@shawn-series-3:~$ lspci | grep Audio
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Trinity HDMI Audio Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)

```

```

shawn@shawn-series-3:~$ aplay -l
aplay: device_list:252: no soundcards found...

```

What can I do? I tried to modprobe the azt one but that didn't work. So... can I uninstall phonon and use alsa purely? If so how do I do that? Thank you for your help guys.

---

### Post by Yellow Pasque on 2013-07-01
> So... can I uninstall phonon and use alsa purely?
Phonon's not the problem. If aplay reports no devices available, then Phonon isn't going to magically find them. Can you give the alsa info? [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by slooksterpsv on 2013-07-03
```

upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.62
!!################################

!!Script ran on: Wed Jul  3 14:30:20 UTC 2013


!!Linux Distribution
!!------------------

Ubuntu 13.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 13.04" NAME="Ubuntu" ID=ubuntu ID_LIKE=debian PRETTY_NAME="Ubuntu 13.04" HOME_URL="http://www.ubuntu.com/" SUPPORT_URL="http://help.ubuntu.com/" BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"


!!DMI Information
!!---------------

Manufacturer:      SAMSUNG ELECTRONICS CO., LTD.
Product Name:      355V4C/356V4C/3445VC/3545VC
Product Version:   P06ABF.009.CP
Firmware Version:  P06ABF


!!Kernel Information
!!------------------

Kernel release:    3.8.0-19-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         x86_64
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     k3.8.0-19-generic
Library version:    1.0.25
Utilities version:  1.0.25


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

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Trinity HDMI Audio Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 01)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!-------------------------------------------------------

00:01.1 0403: 1002:9902
	Subsystem: 144d:c0da
--
00:14.2 0403: 1022:780d (rev 01)
	Subsystem: 144d:c0da


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
snd_hda_intel: model=auto 


!!Loaded sound module options
!!---------------------------


!!ALSA Device nodes
!!-----------------

crw-rw---T+ 1 root audio 116,  1 Jul  3 08:12 /dev/snd/seq
crw-rw---T+ 1 root audio 116, 33 Jul  3 08:12 /dev/snd/timer


!!Aplay/Arecord output
!!--------------------

APLAY

aplay: device_list:252: no soundcards found...

ARECORD

arecord: device_list:252: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!--------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
parport_pc
ppdev
rfcomm
bnep
nls_iso8859_1
joydev
rts5139
uvcvideo
videobuf2_vmalloc
videobuf2_memops
videobuf2_core
videodev
snd_hda_codec_hdmi
snd_hda_intel
snd_hda_codec
snd_hwdep
arc4
kvm_amd
kvm
snd_pcm
ath9k
snd_page_alloc
ath9k_common
ghash_clmulni_intel
snd_seq_midi
snd_seq_midi_event
ath9k_hw
ath
aesni_intel
snd_rawmidi
aes_x86_64
xts
lrw
gf128mul
ablk_helper
cryptd
mac80211
snd_seq
snd_seq_device
snd_timer
snd
fglrx
mac_hid
ath3k
btusb
bluetooth
cfg80211
k10temp
psmouse
soundcore
i2c_piix4
amd_iommu_v2
serio_raw
microcode
lp
parport
r8169
ahci
libahci
wmi
video


!!ALSA/HDA dmesg
!!--------------

[   16.308739] ieee80211 phy0: Atheros AR9485 Rev:1 mem=0xffffc90011f00000, irq=17
[   16.309413] snd_hda_intel 0000:00:01.1: enabling device (0000 -> 0002)
[   16.309423] hda-intel 0000:00:01.1: Force to non-snoop mode
[   16.309513] snd_hda_intel 0000:00:01.1: irq 46 for MSI/MSI-X
[   16.383085] BUG: unable to handle kernel paging request at ffff8801358bbfe0
[   16.383092] IP: [<ffffffffa08f1820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[   16.383100] PGD 1c0e063 PUD 9e054067 PMD 137902063 PTE 80000001358bb161
[   16.383105] Oops: 0003 [#1] SMP 
[   16.383109] Modules linked in: snd_hda_codec_hdmi snd_hda_intel(+) snd_hda_codec snd_hwdep(F) arc4(F) kvm_amd kvm snd_pcm(F) ath9k snd_page_alloc(F) ath9k_common ghash_clmulni_intel(F) snd_seq_midi(F) snd_seq_midi_event(F) ath9k_hw ath aesni_intel(F) snd_rawmidi(F) aes_x86_64(F) xts(F) lrw(F) gf128mul(F) ablk_helper(F) cryptd(F) mac80211 snd_seq(F) snd_seq_device(F) snd_timer(F) snd(F) fglrx(POF) mac_hid ath3k btusb bluetooth cfg80211 k10temp psmouse(F) soundcore(F) i2c_piix4 amd_iommu_v2 serio_raw(F) microcode(F) lp(F) parport(F) r8169 ahci(F) libahci(F) wmi video(F)
[   16.383151] CPU 1 
[   16.383156] Pid: 438, comm: modprobe Tainted: PF          O 3.8.0-19-generic #29-Ubuntu SAMSUNG ELECTRONICS CO., LTD. 355V4C/356V4C/3445VC/3545VC/NP365E5C-S03US
[   16.383160] RIP: 0010:[<ffffffffa08f1820>]  [<ffffffffa08f1820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[   16.383165] RSP: 0018:ffff880137883ac0  EFLAGS: 00010283
--
[   16.383205] Call Trace:
[   16.383211]  [<ffffffffa08f0002>] ? hdmi_pcm_open+0xa2/0x1e0 [snd_hda_codec_hdmi]
[   16.383221]  [<ffffffffa08cf186>] snd_hda_codec_configure+0x146/0x440 [snd_hda_codec]
[   16.383229]  [<ffffffffa07972f0>] azx_probe_continue+0x3a0/0x4f0 [snd_hda_intel]
[   16.383235]  [<ffffffffa07958b0>] ? azx_attach_pcm_stream+0x1e0/0x1e0 [snd_hda_intel]
[   16.383241]  [<ffffffffa0796cb0>] ? azx_halt+0x30/0x30 [snd_hda_intel]
[   16.383246]  [<ffffffffa07956d0>] ? azx_pcm_trigger+0x580/0x580 [snd_hda_intel]
[   16.383252]  [<ffffffffa0796810>] ? azx_runtime_suspend+0x30/0x30 [snd_hda_intel]
[   16.383257]  [<ffffffffa0793670>] ? azx_pcm_free+0x50/0x50 [snd_hda_intel]
[   16.383264]  [<ffffffffa079779a>] azx_probe+0x35a/0x940 [snd_hda_intel]
[   16.383272]  [<ffffffff8137b47b>] local_pci_probe+0x4b/0x80
--
[   16.383320]  [<ffffffff8137a66c>] __pci_register_driver+0x4c/0x50
[   16.383326]  [<ffffffffa01a501e>] azx_driver_init+0x1e/0x1000 [snd_hda_intel]
[   16.383331]  [<ffffffff8100215a>] do_one_initcall+0x12a/0x180
--
[   16.383357] Code: 0f 1f 00 4d 8b bc 24 c0 00 00 00 25 00 e0 00 00 c1 e8 0c 83 c8 01 49 63 17 83 c0 01 83 f8 10 48 8d 14 92 49 8d 14 d7 48 8d 72 08 <66> 89 5a 08 c7 46 08 02 00 00 00 0f 86 5b 02 00 00 48 8d 4e 18 
[   16.383398] RIP  [<ffffffffa08f1820>] patch_generic_hdmi+0xe0/0x550 [snd_hda_codec_hdmi]
[   16.383403]  RSP <ffff880137883ac0>



```

Hmm...

EDIT: This may sound odd, but with Xubuntu and Ubuntu sound works flawlessly, I've only had this issue with Kubuntu and Lubuntu.

---

### Post by Yellow Pasque on 2013-07-03
> Kernel release:    3.8.0-19-generic
Try using the latest raring kernel (3.8.0-25)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)

---

### Post by slooksterpsv on 2013-07-03
If that doesn't help I'll try 3.9 using a mainline kernel

---

### Post by slooksterpsv on 2013-07-04
Upgrading helped, I hadn't ran my updates yet so yeah that fixed it.

Thanks! =D

---

